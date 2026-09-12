# モデル重みの利用条件について

更新日：2026-09-12

Virtual Headの公開ZIPには学習済みONNXモデルを含めません。「標準モデルをダウンロード」を押した場合だけ、各モデルの公式GitHub Releaseから利用者のPCへ直接取得します。

## 使用モデルと謝辞

Virtual Headの頭部検出・回転角推定は、PINTO0309氏（Katsuya Hyodo氏）が公開しているプロジェクトとモデルを利用しています。研究・実装・モデル公開に感謝します。

- [High-Angle Robust Fast Face Alignment（HRFFA）](https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment)
- [HRFFA公式weights Release](https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment/releases/tag/weights)
- [YOLO-Wholebody34](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/471_YOLO-Wholebody34)
- [Gold-YOLO-Head](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/421_Gold-YOLO-Head)（任意検出器）
- [PINTO0309 / YOLO](https://github.com/PINTO0309/YOLO)
- [YawNet](https://github.com/PINTO0309/YawNet)
- [YawNet公式resources Release](https://github.com/PINTO0309/YawNet/releases/tag/resources)

モデル重みはVirtual Headとは別の著作物です。Virtual Headおよびtattoは、各モデル重みのライセンス解釈、利用、商用利用、改変、再配布が特定の用途で許可されることを保証しません。ダウンロード前に、利用者自身が公式配布ページ、リポジトリのライセンス、モデル固有の説明、学習データ等の条件を確認し、使用可否を判断してください。アプリのダウンロード機能は取得と改ざん検知を補助するだけで、権利や許諾を付与しません。

## 標準モデルと確認先

| 用途 | ダウンロードするファイル | 利用者が確認する公式情報 |
|---|---|---|
| 頭部検出 | `yolov9_t_wholebody34_0100_1x3x640x640.onnx` | [YOLO-Wholebody34のモデル説明](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/471_YOLO-Wholebody34)、[同フォルダのLICENSE](https://github.com/PINTO0309/PINTO_model_zoo/blob/main/471_YOLO-Wholebody34/LICENSE)、[HRFFA weights Release](https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment/releases/tag/weights) |
| 頭部回転角 | `yawnet_distill_128_unified_v6u_1x3x128x128.onnx` | [YawNet](https://github.com/PINTO0309/YawNet)、[YawNet LICENSE](https://github.com/PINTO0309/YawNet/blob/main/LICENSE)、[YawNet resources Release](https://github.com/PINTO0309/YawNet/releases/tag/resources) |

## 任意のGold-YOLO-N Head

Virtual Head 0.1.0-alpha.10以降は、Gold-YOLO-N Headの固定入力ONNXを外部モデルとして選択できます。推奨した試験ファイルは`gold_yolo_n_head_0277_0.5071_1x3x192x320.onnx`です。モデルはVirtual HeadのZIP、標準ダウンロード、GitHub Releaseへ含めません。

公式の`421_Gold-YOLO-Head`フォルダにはGPL-3.0の`LICENSE`が置かれています。利用者は[モデル説明](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/421_Gold-YOLO-Head)、[LICENSE](https://github.com/PINTO0309/PINTO_model_zoo/blob/main/421_Gold-YOLO-Head/LICENSE)、[公式ダウンロードスクリプト](https://github.com/PINTO0309/PINTO_model_zoo/blob/main/421_Gold-YOLO-Head/download_n.sh)を確認し、自分の用途での使用、商用利用、改変、配布の可否を判断してください。アプリがONNX形式に対応していることは、モデルに対する権利や許諾を意味しません。

固定している容量とSHA-256は、ダウンロードしたファイルがVirtual Headで検証したファイルと同一かを確認するための情報です。ライセンスの適用範囲や利用許諾を証明するものではありません。

| ファイル | 容量 | SHA-256 |
|---|---:|---|
| `yolov9_t_wholebody34_0100_1x3x640x640.onnx` | 8,192,670 bytes | `7dd9b514426b33423ffbc4e22fb6127f2145686441f2c398170585363c009575` |
| `yawnet_distill_128_unified_v6u_1x3x128x128.onnx` | 3,078,957 bytes | `ccbe06474df5701263d09fdb48af4703fd1c3f67e5934521984f1f455ae75dc6` |

`licenses/YOLO_WHOLEBODY34_LICENSE.txt`と`licenses/YAWNET_LICENSE.txt`は、確認を助けるため各公式リポジトリから取得したライセンス文の写しです。これらを同梱しても、その文面が学習済み重みや利用者の用途へ適用されるとVirtual Headが判断・保証するものではありません。公式側の表示が更新された場合は公式情報を優先してください。

## その他のモデル・素材

- 自作または第三者のONNXを指定する場合も、入手元と利用条件を利用者自身で確認してください。
- Minecraft互換Skin PNG、VRM、MMD、FBXは作品ごとに作者、キャラクター、配布、動画利用等の条件が異なります。Virtual Headは第三者素材を同梱しません。
- `vendor/hrffa_onnx.py`など、アプリに組み込む第三者コードとライブラリの表示は`THIRD_PARTY_NOTICES.txt`を確認してください。
