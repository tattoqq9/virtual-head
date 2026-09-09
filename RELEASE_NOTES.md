# 0.1.0-alpha.6

最初のGitHub公開プレリリースです。

## 含まれる機能

- 画像、動画、カメラ入力
- Minecraft互換SkinのVoxel頭部Overlay
- Yaw追従、固定Pitch、Roll補助オプション
- 頭の拡大率・位置・平滑化調整
- CPU／NVIDIA CUDA
- 動画・画像保存、FFmpeg指定時のH.264・入力音声保存
- 画面画像7枚を使ったローカルHTMLガイド
- 入力上限、既知モデルSHA-256照合、SBOM、依存関係監査
- Cythonネイティブ拡張による独自モジュールの保護

## 確認済み

- Windows 11 x64の開発PC
- 45件の自動テスト
- 保護版EXEのGUI自己診断
- CUDAでテスト動画の頭部検出・Yaw推定・合成
- ZIPの全ファイルCRCと、モデル・Skin・個人データ・開発ソース非同梱

## 既知の制限

- 学習済みONNXモデルは同梱していません。
- 未署名のプレリリースです。
- 実カメラと別PCでの動作確認は限定的です。
- Pitch自動追従、前景復元、仮想カメラ、VRM/MMD/FBXは未対応です。

## ダウンロード

- `VirtualHead-0.1.0-alpha.6-windows-x64.zip`
- `VirtualHead-0.1.0-alpha.6-windows-x64.zip.sha256`

SHA-256：

```text
feb5457a2c5e13d6f368f3feca95243cf0d0854ec407e3c74fa51e22b0dcd4a4
```

ダウンロードしたZIPは、Releaseに添付した`.sha256`と照合してください。
