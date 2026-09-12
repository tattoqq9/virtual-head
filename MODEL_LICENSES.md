# モデル・素材のライセンス

調査日：2026-09-12

Virtual Head 0.1.0-alpha.9の公開ZIPにはONNXを含めません。利用者がアプリの「標準モデルをダウンロード」を押した場合だけ、PINTO0309氏の公式GitHub Releaseから次の2ファイルを取得します。取得後は容量とSHA-256を検証し、一致しないファイルは使用しません。

| 用途 | 標準モデル | ライセンスと根拠 |
|---|---|---|
| 頭部検出 | `yolov9_t_wholebody34_0100_1x3x640x640.onnx` | MIT。`471_YOLO-Wholebody34`はモデルをMITと明記し、同フォルダにMIT全文を掲載。HRFFAも、この系列を公式GPL版ではなくPINTO0309氏のMIT版YOLO実装で学習した再配布可能なモデルと説明 |
| 頭部回転角 | `yawnet_distill_128_unified_v6u_1x3x128x128.onnx` | MIT。YawNet公式リポジトリはMITを明記し、公式`resources` ReleaseでこのONNXを配布。Virtual Headで固定したファイルと公式YawNet版は容量3,078,957 bytes、SHA-256 `ccbe06474df5701263d09fdb48af4703fd1c3f67e5934521984f1f455ae75dc6`が一致 |
| 推論コード | `vendor/hrffa_onnx.py` | MIT、Copyright (c) 2026 Katsuya Hyodo |

MITは利用、変更、複製、配布、サブライセンス、販売を認めます。再配布時は著作権表示とMIT許諾文を残す必要があります。Virtual Headは次の原文をアプリ内と配布フォルダの`licenses`に収録します。

- `YOLO_WHOLEBODY34_LICENSE.txt`：Copyright (c) 2024 Kin-Yiu, Wong and Hao-Tang, Tsui／Copyright (c) 2025 Katsuya Hyodo
- `YAWNET_LICENSE.txt`：Copyright (c) 2026 Katsuya Hyodo
- `HRFFA_LICENSE.txt`：Copyright (c) 2026 Katsuya Hyodo

今回選んだYOLOv9-tは、公式の`WongKinYiu/yolov9`を直接利用したGPL版モデルではありません。PINTO0309氏のMIT版実装で学習されたWholebody34モデルです。別リポジトリや別ファイルにGPL-3.0と表示されたYOLOv9モデルへ差し替える場合、その条件は自動的には引き継がれないため、配布前に個別確認が必要です。

標準以外のモデルについては、ファイルごとの条件が優先されます。

| 対象 | 配布方針 |
|---|---|
| `deimv2_*wholebody49*.onnx`、`hrffa_*.onnx`、DINOv3由来モデル | 標準配布には使用しない。各モデル・学習元・教師モデルの条件を確認してから扱う |
| 利用者が選ぶ自作・第三者ONNX | Virtual Headは権利を付与しない。利用者が正当に入手した互換モデルだけを指定する |
| Minecraft互換Skin PNG | 画像ごとに作者・キャラクター権利・配布条件が異なる。第三者Skinは同梱しない |
| VRM / MMD / FBX | モデルごとの利用規約に従う。現在のWindows製品版には同梱しない |

参照先：

- YOLO-Wholebody34説明・モデルのMIT表示：https://github.com/PINTO0309/PINTO_model_zoo/tree/main/471_YOLO-Wholebody34
- YOLO-Wholebody34ライセンス原文：https://github.com/PINTO0309/PINTO_model_zoo/blob/main/471_YOLO-Wholebody34/LICENSE
- MIT版YOLO実装：https://github.com/PINTO0309/YOLO
- HRFFAのモデル説明・公式weights：https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment
- YawNet説明・MIT表示：https://github.com/PINTO0309/YawNet
- YawNetライセンス原文：https://github.com/PINTO0309/YawNet/blob/main/LICENSE
- YawNet公式resources Release：https://github.com/PINTO0309/YawNet/releases/tag/resources

この記録は確認時点の配布条件をまとめたものです。標準モデルのURL、ファイル、ハッシュ、上流ライセンスが変わった場合は、次のRelease前に再確認します。
