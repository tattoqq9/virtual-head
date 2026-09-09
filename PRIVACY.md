# Virtual Head プライバシー方針

最終更新：2026-09-08  
提供者：tatto

Virtual Headは画像、動画、カメラ映像を利用者のWindows PC内で処理します。現在のWindows版には、映像、推論結果、利用統計、診断情報をtattoまたは第三者のサーバーへ送信する機能はありません。広告、アカウント、遠隔測定、更新確認機能もありません。

## PC内に保存する情報

- `%LOCALAPPDATA%\VirtualHead\settings.json`：選択したモデル、Skin、画像、動画、出力先、FFmpeg、CUDA DLLフォルダなどのローカルパスと画面設定
- `%LOCALAPPDATA%\VirtualHead\app.log`：処理エラーと診断情報。エラー内容にローカルパスが含まれる場合があります
- 利用者が選んだ出力先：合成画像または動画、`tracking.jsonl`、`run.json`
- `%LOCALAPPDATA%\VirtualHead\gui_smoke.json`、`self_test_result.json`：開発者向け自己診断を明示的に実行した場合のみ

保存結果には頭部位置や回転角、選択ファイルの絶対パス、処理設定、モデルのSHA-256が含まれます。共有前に `run.json` と `tracking.jsonl` を確認してください。

## カメラと外部プログラム

カメラは利用者が「開始」を押してカメラ入力を選択した場合だけ開きます。停止またはアプリ終了時に解放します。カメラ録画は初期状態では保存されず、「結果を保存する」を選択した場合だけ保存します。

利用者がFFmpegを指定した場合、Virtual Headは動画変換のためそのローカル実行ファイルを起動します。指定したFFmpeg自体の動作は、その配布元の方針に従います。

## 削除

Virtual Headを終了し、`%LOCALAPPDATA%\VirtualHead` と利用者が指定した出力フォルダを削除すると、Virtual Headが保存した設定、ログ、処理結果を削除できます。元の画像、動画、モデル、SkinはVirtual Headが管理するファイルではありません。

将来ネットワーク機能や自動更新、クラッシュレポートを追加する場合は、送信を開始する前にこの文書とアプリ画面を更新し、送信対象と選択方法を示します。
