# 0.1.0-alpha.10（準備中）

- Gold-YOLO-N Headの生出力版`[1,A,6]`と後処理済み版`[N,7]`に対応
- 192×320生出力版で現在のテスト動画341/341フレームを検出
- 検出器単体の中央値はDirectML 1.32ms、CPU 4.55ms
- Windows配布ランタイムをONNX Runtime DirectML 1.24.4へ固定
- Gold-YOLO-Nは外部モデル選択のみ。モデル本体はZIPや標準ダウンロードへ含めない
- Gold-YOLO-Headの公式説明、GPL-3.0 LICENSE、性能比較へのリンクを追加
- 配布ZIPは約100.7MB、モデル重みと第三者Skinを含まない
- 55件の自動テスト、完成EXEのGUI起動、Gold-YOLO-NとYawNetのDirectML実行を確認

## ダウンロード

- `VirtualHead-0.1.0-alpha.10-windows-x64.zip`
- `VirtualHead-0.1.0-alpha.10-windows-x64.zip.sha256`

SHA-256：

```text
5c0a82ecc4cc37684ec3f97cd22c95444fc5adccb87783fee8c3e39a53a7ce2d
```

Gold-YOLO-Nのモデルは別途、公式配布元とライセンスを確認して取得してください。標準モデルを使う場合は、従来どおりアプリ内の「標準モデルをダウンロード」を使用できます。

# 0.1.0-alpha.9（未公開）

- 標準の頭部検出器を約8.2MBの`yolov9_t_wholebody34_0100_1x3x640x640.onnx`へ変更
- YOLOv9-tとYawNet 128の合計ダウンロード量を約80MBから約11MBへ削減
- DirectMLで頭部検出とYawNetをGPU実行できるようにし、NVIDIA、AMD、IntelのDirectX 12対応GPUを対象化
- YOLO-Wholebody34とYawNetの公式説明・Release・ライセンス確認先を追加
- ダウンロード元を公式Releaseへ固定し、容量・SHA-256検証を継続

モデル重みの利用条件はVirtual Head本体とは別です。各利用者が公式情報を確認し、予定する利用・商用利用・再配布が許可されるかを判断してください。ダウンロード機能は権利や許諾を保証しません。

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
