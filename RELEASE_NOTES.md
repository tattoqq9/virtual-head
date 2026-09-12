# 0.1.0-alpha.9（準備中）

- 標準の頭部検出器を約8.2MBの`yolov9_t_wholebody34_0100_1x3x640x640.onnx`へ変更
- YOLOv9-tとYawNet 128の合計ダウンロード量を約80MBから約11MBへ削減
- DirectMLで頭部検出とYawNetをGPU実行できるようにし、NVIDIA、AMD、IntelのDirectX 12対応GPUを対象化
- YOLO-Wholebody34とYawNetの公式MIT表示を確認し、著作権表示とライセンス原文を追加
- ダウンロード元を公式Releaseへ固定し、容量・SHA-256検証を継続

使用するYOLOv9-tはPINTO0309氏のMIT版YOLO実装で学習されたWholebody34モデルです。GPL-3.0で公開されている別系統のYOLOv9モデルは使用していません。

# 0.1.0-alpha.8

別PCでの初回利用に必要な案内を追加し、NVIDIA GPUを優先する自動実行モードを初期値にしました。

## 主な変更

- 「自動（GPU優先）」を初期値に設定
- CUDAを利用できる場合は頭部検出とYawNetの両方をGPUで実行
- CUDAの初期化に失敗した場合はCPUへ自動でフォールバック
- 実際の実行デバイスを画面の状態表示と`run.json`の`active_device`へ記録
- alpha.7の初期CPU設定を初回のみ自動設定へ移行。alpha.8で明示的にCPUを選んだ場合は維持
- GitHub Releaseへの移動、正しいZIP、モデル取得、SmartScreenの確認を説明する画像を追加
- アプリ内ガイドを7枚から10枚へ更新
- コード署名とMicrosoft Store配布の方針を追加

## 確認済み

- 51件の自動テスト
- 完成EXEで動画1フレームを処理し、頭部を1/1検出
- NVIDIA CUDA指定環境で検出・YawNetの両方が`CUDAExecutionProvider`を使用
- 同じフレームの実測でCPU約0.87 fps、GPU約12.29 fps
- CUDAランタイムを利用できない場合のCPUフォールバック
- ZIPの全ファイルCRC
- 公開ZIPにONNX、第三者Skin、ユーザー情報、開発用Pythonソースが含まれないこと
- アプリ固有の10モジュールをCythonネイティブ拡張として収録

## GPUについて

CUDA実行にはNVIDIAドライバー、CUDA 12.x、cuDNN 9.xが必要です。CUDA/cuDNNは容量が大きいためZIPに同梱していません。利用できない環境ではCPUで動作します。

AMD・Intel GPU向けDirectMLも検証しましたが、現在のDEIMv2頭部検出モデルに非対応の演算があるため、この版では使用しません。

## モデルについて

公開ZIPは学習済みONNXを同梱しません。利用者がアプリの「標準モデルをダウンロード」を押したときだけ、PINTO0309氏の公式GitHub Releaseへ接続します。映像、画像、Skin、推論結果は送信しません。

モデルのコードと学習済み重みの条件は同一とは限りません。特に商用利用を予定する場合は、`MODEL_LICENSES.md`を確認してください。

## 既知の制限

- コード署名のないプレリリースのため、SmartScreenが「不明な発行元」と表示する場合があります。GitHub公式ReleaseとSHA-256を確認してください。
- 実カメラと複数構成の別PCでの動作確認は限定的です。
- CPU処理は動画の実時間速度を下回る場合があります。
- Pitch自動追従、前景復元、仮想カメラ、VRM/MMD/FBXは未対応です。

## ダウンロード

- `VirtualHead-0.1.0-alpha.8-windows-x64.zip`
- `VirtualHead-0.1.0-alpha.8-windows-x64.zip.sha256`

SHA-256：

```text
af7f74e2263e280fb055512cb7d2245fbf38a62632ec7efda4c02c399e633a71
```

ダウンロードしたZIPは、Releaseに添付した`.sha256`と照合してください。

## SmartScreen警告を解除して起動する

1. SHA-256が上記の値と一致することを確認します。
2. ZIPを右クリックして「プロパティ」を開き、全般タブ下部に「許可する」または「ブロックの解除」があればチェックして「適用」します。
3. ZIPを「すべて展開」します。すでに展開していた場合も、解除したZIPから展開し直します。
4. `VirtualHead.exe`を起動し、「WindowsによってPCが保護されました」で「詳細情報」→「実行」を選びます。

画像付きの詳しい手順は[README](https://github.com/tattoqq9/virtual-head#smartscreenの警告)を参照してください。SmartScreen自体を無効にする必要はありません。
