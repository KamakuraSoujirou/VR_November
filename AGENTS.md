# VR_November — AIエージェント向けガイド

このファイルは Claude Code / Cursor / Copilot / Gemini など、すべてのAIツール共通の指示書です。
（CLAUDE.md と GEMINI.md はこのファイルを読み込んでいるだけなので、編集はここだけでOK）

## プロジェクト概要
- ゲーム名: VR_November
- ジャンル / 概要: （ここに書く）
- Unity バージョン: 6000.3.10f1
- 作成日: 2026-11-20

## フォルダ構成
このリポジトリは**公開**です。画像・音声などのアセットは、非公開リポジトリ
（`VR_November-assets`）を Git サブモジュールとして `Assets/_PrivateAssets/` に入れています。

公開（このリポジトリ）
- `Assets/_Project/Scripts/` … 自作の C# スクリプト
- `Assets/_Project/Scenes/` … シーン
- `Assets/_Project/Prefabs/` … プレハブ

非公開（サブモジュール `Assets/_PrivateAssets/`）
- `Art/` … 画像・テクスチャ・マテリアル・UI素材
- `Audio/` … BGM・効果音
- `Models/` … 3Dモデル・アニメーション
- `ThirdParty/` … アセットストア等の購入・配布アセット（再配布不可）

## コーディング規約（C#）
- クラス・メソッド・プロパティは PascalCase、ローカル変数・引数は camelCase、private フィールドは `_camelCase`
- インスペクターに出すフィールドは `public` ではなく `[SerializeField] private` を使う
- `Update()` 内で `GetComponent` / `Find` 系を呼ばない（`Awake` / `Start` でキャッシュする）
- 1ファイル1クラス。ファイル名とクラス名を一致させる
- コメントは日本語でOK

## AIへのルール
- `Library/`, `Temp/`, `Logs/`, `UserSettings/` の中身は読まない・編集しない
- アセットを作成・移動・削除するときは、対応する `.meta` ファイルも必ず一緒に扱う（GUIDが壊れるため）
- `.unity` / `.prefab` / `.asset` のYAMLは、頼まれない限り直接編集しない
- 画像・音声・モデル・購入アセットは必ず `Assets/_PrivateAssets/` 以下に置く（公開リポジトリに入れない）
- `Assets/_PrivateAssets/` 内の変更は、サブモジュール側でコミット & push してから、本体側でサブモジュールの更新をコミットする
- パッケージの追加（`Packages/manifest.json` の変更）は事前に確認すること
- 変更後はコンパイルエラーが出ないか確認し、変更点を簡潔に説明すること
