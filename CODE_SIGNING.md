# Virtual Headのコード署名方針

調査日：2026-09-10

## 現在の状態

GitHubで配布しているプレリリースは未署名です。Microsoft Defender SmartScreenは、署名されていない新しい実行ファイルを「不明な発行元」と表示します。ファイル内容が変わるとハッシュも変わるため、未署名版はバージョンごとに評価が最初から始まります。自己署名証明書では一般利用者の警告を解消できません。

## 現在の判断

2026-09-10時点では、有料のコード署名は導入しません。GitHub Release、SHA-256、SmartScreenの「詳細情報」から起動する手順を案内します。無料で確実な署名経路が利用可能になった場合、またはMicrosoft Store配布を始める場合に再検討します。

## 推奨する公開経路

### 1. Microsoft Store

日本の個人開発者にとって最も進めやすい方法です。個人開発者登録は現在無料で、政府発行IDと自撮りによる本人確認が必要です。Store配布アプリはMicrosoftの証明書で再署名されるため、SmartScreenのダウンロード警告を避けられます。

開始場所：<https://storedeveloper.microsoft.com/>

tattoが行う必要がある作業：

1. 個人用Microsoftアカウントで開始する。
2. `Individual developer`を選択する。
3. 政府発行IDと自撮りで本人確認する。
4. Partner CenterのApps & Games画面へ入れる状態にする。
5. 公開時に表示されるPublisher名を確認する。

アカウントが用意できた後、Virtual Head側ではMSIXのIdentity、Publisher ID、署名、Store提出用説明・画像を合わせる。

### 2. Microsoft Artifact Signing

GitHubのZIPを直接署名する場合のMicrosoft推奨サービスです。Basicは1アカウント月額9.99米ドルで月5,000署名です。ただしPublic Trustの個人開発者は現在米国・カナダ居住者に限られ、日本では登録済み組織としての確認が必要です。組織で利用する場合、本人・組織確認には通常1〜20営業日以上かかる場合があります。

### 3. 信頼されたCAのコード署名証明書

日本の個人または事業者へ証明書を発行できる認証局からRSAコード署名証明書を取得し、Windows SDKの`signtool.exe`でEXE、DLL、MSIXへ署名する方法です。証明書費用、本人確認、秘密鍵のハードウェアまたはクラウド保管方法を認証局ごとに比較する必要があります。

## 署名後の検査

- `signtool verify /pa /all /v VirtualHead.exe`
- SHA-256タイムスタンプを付ける。
- EXEだけでなく、実行時に読み込む独自`.pyd`とインストーラーも署名する。
- 署名後にファイルを変更せず、完成物のSHA-256を生成する。
- Smart App ControlとSmartScreenが有効なWindows 11で全機能を確認する。

## 公式資料

- SmartScreen reputation: https://learn.microsoft.com/windows/apps/package-and-deploy/smartscreen-reputation
- Microsoft Store個人開発者登録: https://learn.microsoft.com/windows/apps/publish/whats-new-individual-developer
- Artifact Signingの準備: https://learn.microsoft.com/azure/artifact-signing/quickstart
- Artifact Signingの料金: https://learn.microsoft.com/azure/artifact-signing/how-to-change-sku
