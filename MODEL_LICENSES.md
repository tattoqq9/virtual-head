# モデル・素材の配布条件

調査日：2026-09-09

Windows版はONNXを利用者がローカルで選択して実行できますが、配布ZIPにはモデルを含めません。コードのライセンスと学習済み重みの条件は別です。公開前に、このファイルと配布ZIPの内容が一致することを確認します。

| 対象 | 確認できた情報 | Windows ZIPへの判断 |
|---|---|---|
| `vendor/hrffa_onnx.py` | 元リポジトリのコードはMIT、Copyright (c) 2026 Katsuya Hyodo | MIT全文を同梱して配布可 |
| `deimv2_*wholebody49*.onnx` | 配布元のPINTO_model_zoo `488_DEIMv2-Wholebody49/LICENSE`はApache-2.0を明記。一方、現在のDEIMv2本家は非商用限定で、DINOv3由来物にはDINOv3条件も関係する | モデル固有表示と上流条件の関係を配布者へ確認するまで公開ZIPへ入れない |
| `yawnet_distill_*.onnx` | YawNetはHRFFA公式weights releaseで配布されているが、READMEはコードをMITとしつつ派生重みの条件確認を求めている。使用中の重み単体のライセンス表示はない | 重み単体の再配布許諾が明記されていないため未同梱。権利者から配布条件を確認するまで公開ZIPへ入れない |
| `hrffa_*.onnx` | コードはMIT。HRFFA READMEはDINOv3/DEIMv2由来重みについて、学習済みHRFFA重み・ONNXを配る前に派生物条件を確認するよう明記 | 派生重みの条件確認が終わるまで未同梱 |
| DINOv3公式教師重み | DINOv3独自ライセンスは同条件での再配布を認めるが、制約・補償条項がある。HRFFAは教師重みを同梱しない | Virtual Headには教師重み自体を同梱しない。派生重みに適用される条件は権利者へ確認 |
| `yolov9_{n,t}_wholebody34_*.onnx` | HRFFA READMEは、PINTO0309/YOLOによるMIT実装で学習したモデルとして再配布可能と明記 | 将来の小型検出器候補。現Windowsバックエンドとの入出力互換対応・精度試験・MIT表示を終えてから採用 |
| Minecraft Skin PNG | 画像ごとに作者・キャラクター権利・配布条件が異なる | 手続き生成の標準頭部だけを同梱。第三者Skinは権利確認なしに同梱しない |
| VRM / MMD / FBX | モデルごとの利用規約に従う。Windows版の製品機能には未採用 | 同梱しない |

参照先：

- HRFFAコード・重みの説明・ライセンス：https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment
- HRFFA weights release：https://github.com/PINTO0309/High-Angle_Robust_Fast_FaceAlignment/releases/tag/weights
- DINOv3 License：https://github.com/facebookresearch/dinov3/blob/main/LICENSE.md
- DEIMv2：https://github.com/Intellindust-AI-Lab/DEIMv2
- DEIMv2-Wholebody49固有ライセンス：https://github.com/PINTO0309/PINTO_model_zoo/blob/main/488_DEIMv2-Wholebody49/LICENSE
- MIT版YOLOv9実装：https://github.com/PINTO0309/YOLO
- YOLOv9-Wholebody34：https://github.com/PINTO0309/PINTO_model_zoo/tree/main/455_YOLOv9-Wholebody34

モデルを同梱する版を作るときは、モデル名・取得元・バージョンまたはSHA-256・ライセンス全文・NOTICE・変更内容を配布物へ追加します。モデルを自動ダウンロードする場合も、取得先の規約と、利用者へのライセンス提示・同意要件を確認します。
