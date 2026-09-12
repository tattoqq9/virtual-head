# Gold-YOLO-N Head対応結果

更新日：2026-09-12

Virtual Head 0.1.0-alpha.10は、PINTO0309氏が公開しているGold-YOLO-N Headの固定入力ONNXに対応します。生出力`[1,A,6]`（`cx,cy,w,h,class,score`）と、後処理済み出力`[N,7]`（`batch,class,x1,y1,x2,y2,score`）を自動判定します。

## 推奨した試験ファイル

`gold_yolo_n_head_0277_0.5071_1x3x192x320.onnx`

- 入力：`1×3×192×320`
- 容量：22,516,137 bytes
- SHA-256：`b52e639ce8a5d2cf5a70aeede7f94c830583558cf8563d4e908e04b7a109e452`
- 形式：生出力版。NMSはVirtual Head側で実行
- 選択方法：「モデル」タブの「頭部検出モデル」から上記ONNXを選ぶ

モデル名やハッシュは今回試験したファイルを特定するための情報です。権利や許諾を証明するものではありません。

## 現在のテスト動画での比較

入力は1920×1080、341フレームの`test1.mp4`、しきい値0.5です。GPUはDirectML、CPUはONNX Runtime CPU Execution Providerを使用しました。時間は検出器のONNX呼び出しのみで、動画読込、YawNet、追跡、Voxel描画、保存を含みません。

| 検出器 | 検出フレーム | DirectML中央値 | CPU中央値 | モデル容量 |
|---|---:|---:|---:|---:|
| YOLOv9-t Wholebody34 640×640（標準） | 341/341 | 6.41ms | 25.57ms | 8,192,670 bytes |
| Gold-YOLO-N 192×320 生出力 | 341/341 | 1.32ms | 4.55ms | 22,516,137 bytes |
| Gold-YOLO-N 192×320 後処理済み | 341/341 | 2.54ms | 5.13ms | 22,522,741 bytes |
| Gold-YOLO-N 320×320 生出力 | 301/341 | 1.79ms | 7.05ms | 22,529,581 bytes |
| Gold-YOLO-N 384×640 生出力 | 341/341 | 3.06ms | 13.16ms | 22,576,635 bytes |

192×320生出力版は全フレームを検出し、検出器単体では標準モデルよりDirectMLで約4.8倍、CPUで約5.6倍高速でした。ファイル容量は約2.75倍です。320×320版は16:9映像を正方形へ直接リサイズする影響が大きく、この動画では40フレームを検出できませんでした。

後処理済み版はDirectMLセッションで動作しましたが、後処理の一部がCPUへ配置されました。生出力版は全推論ノードがDirectMLへ配置され、Python側のNMSを含めても今回の候補で最速でした。

Minecraft SkinのOverlayも192×320生出力版とYawNet 128の組み合わせで341/341フレームを追跡できました。頭部枠のYOLOv9-tとの平均IoUは0.883、平均面積比は0.992でした。全体の処理速度はVoxel描画、1920×1080動画保存等にも左右されるため、検出器単体の倍率がそのままアプリ全体の倍率にはなりません。

## 配布とライセンス

Gold-YOLO-Headの[公式フォルダ](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/421_Gold-YOLO-Head)にはGPL-3.0の[LICENSE](https://github.com/PINTO0309/PINTO_model_zoo/blob/main/421_Gold-YOLO-Head/LICENSE)が置かれています。公式`download_n.sh`は複数の変換済みモデルを含む約1.37GBのアーカイブを取得します。

Virtual Headは非公開ソースで配布する方針のため、このモデルをZIPへ同梱せず、標準モデルのワンクリック取得にも追加しません。利用する場合は、利用者が[公式説明と配布物](https://github.com/PINTO0309/PINTO_model_zoo/tree/main/421_Gold-YOLO-Head)を確認して取得し、自分の用途に適用される条件を判断したうえでローカルONNXを選択してください。
