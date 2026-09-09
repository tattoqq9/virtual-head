# Virtual Head

Virtual Headは、画像・動画・カメラの実写頭部へ、Minecraft互換SkinのVoxel頭部を重ねるWindowsアプリです。頭部の位置、大きさ、Yaw（左右の回転）をONNXモデルで推定し、体と背景を実写のまま残します。

![Virtual Headの画面](guide/images/01_overview.png)

> [!WARNING]
> 現在は開発者向けプレリリースです。学習済みONNXモデルはライセンス確認中のため配布物に含まれません。対応モデルを正当に入手済みのテスターを対象とします。

## 主な機能

- PNG／JPEG／BMP／WebP画像への合成
- 動画への合成と、FFmpeg指定時のH.264・入力音声保存
- カメラのリアルタイムプレビューと録画
- Minecraft互換Skin PNGの頭部6面と髪・帽子レイヤー
- 頭の大きさ、位置、固定Pitch、追従平滑化の調整
- CPUおよびNVIDIA CUDA実行
- 画像・動画・モデルの入力検査と既知モデルのSHA-256照合
- PC内だけでの処理。アカウント、広告、遠隔測定なし

## ダウンロードと起動

1. GitHubの[Releases](https://github.com/tattoqq9/virtual-head/releases)から最新の`VirtualHead-*-windows-x64.zip`と`.sha256`をダウンロードします。
2. ZIPを展開します。`VirtualHead.exe`と`_internal`フォルダを分離しないでください。
3. `VirtualHead.exe`を起動します。
4. 「モデル」タブで対応する頭部検出ONNXと回転角ONNXを指定します。
5. 入力とSkinを選び、「開始」を押します。

Windows x64用です。Pythonのインストールは不要です。未署名プレリリースのため、Windowsから発行元未確認の警告が表示される場合があります。ダウンロードしたファイルのSHA-256をRelease記載値と照合してください。

## 使い方

アプリ画面下の「使い方」ボタンから、7枚の画面画像を使ったガイドを開けます。リポジトリ内の[USER_GUIDE.html](USER_GUIDE.html)も同じ内容です。

### 動画

![動画入力](guide/images/02_video.png)

「動画」を選択し、動画、Skin、保存先を指定して開始します。FFmpegを指定するとH.264へ変換し、入力音声を残せます。

### 画像

![画像入力](guide/images/03_image.png)

「画像」を選択して開始すると1枚だけ処理し、`overlay.png`、`tracking.jsonl`、`run.json`を保存します。

### カメラ

![カメラ入力](guide/images/04_camera.png)

通常はカメラ番号`0`を使用します。カメラ録画に音声は入りません。

### モデル

![モデル設定](guide/images/05_models.png)

任意のONNXが使えるわけではなく、Virtual Headの入出力仕様に合うモデルが必要です。検証に使用したファイル名と再配布判断は[MODEL_LICENSES.md](MODEL_LICENSES.md)を参照してください。

### 見た目

![見た目の設定](guide/images/06_appearance.png)

頭の拡大率の初期値は`18%`です。保存済み設定がある場合は保存値を優先します。

## プレリリースの制限

- Yawは自動追従しますが、Pitchは固定設定です。
- 手や物体が顔の前を横切る場合の前景復元には対応していません。
- カメラ録画は公称FPSを使うため、処理が追いつかないPCでは実時間とずれる場合があります。
- 仮想カメラ、VRM、MMD、FBXのOverlayはこのWindows配布版に含まれません。
- モデル、第三者Skin、単体FFmpeg、CUDA/cuDNNは同梱していません。

## プライバシーとセキュリティ

画像、動画、カメラ映像は利用者のPC内で処理されます。現在の版には映像、診断情報、利用統計を外部送信する機能はありません。詳しくは[PRIVACY.md](PRIVACY.md)と[SECURITY.md](SECURITY.md)を参照してください。

不具合は[GitHub Issues](https://github.com/tattoqq9/virtual-head/issues)へ報告できます。ログや`run.json`にはローカルのユーザー名やファイルパスが含まれる場合があるため、公開前に内容を確認してください。未修正の脆弱性は公開Issueではなく、[GitHubの非公開Security Advisory](https://github.com/tattoqq9/virtual-head/security/advisories/new)から報告してください。

## ライセンスと権利表示

Virtual Head本体は[MIT License](LICENSE)、Copyright © 2026 tattoです。この公開リポジトリはバイナリ配布と問題報告用で、開発ソースコードは含みません。

第三者コードとライブラリはそれぞれのライセンスに従います。[THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt)と配布ZIP内の`licenses`を確認してください。モデルと素材の条件は[MODEL_LICENSES.md](MODEL_LICENSES.md)にまとめています。

Virtual Headは公式Minecraft製品ではなく、MojangまたはMicrosoftの承認・提携を受けていません。Minecraftの名称は、利用者が用意する互換Skin PNG形式の説明として使用しています。公式素材は配布物に含みません。
