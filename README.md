# Multi-Resolution Character Transfer

一人のキャラクターの identity を保ったまま、実写 → 2Dアニメ → 高精細ピクセルアート → 低解像度ピクセルアート → 極低解像度スプライト、と**情報密度だけを段階的に落として**変換するワークフローです。落とした解像度を元に戻して帰ってくる一発撮り動画プロンプトまで、一連で設計します。

Preserves one character's identity while changing only the rendering medium and information density — live action, 2D animation, high-detail pixel art, low-resolution pixel art, and an extreme low-resolution sprite — then restores the original form.

リブートや着せ替えではなく、**同じ人物の別レンダリング**であることをプロンプト全体で強制します。

## できること / What you get

- キャラクター不変条件（髪型・年齢感・体型・配色・象徴小物）の抽出
- 状態ごとの単体リファレンス画像プロンプト（キャラは白背景、背景は人物なしで別作り）
- `@Image 1` … の形に割り当てたリファレンスマップ
- 30秒・一発撮りの動画プロンプト（既定は Seedance 2.5、タイムスタンプ付き 6〜9 ビート）
- 解像度に合わせて変化するカメラ言語、および音質の劣化／復元デザイン
- 生成前に通す連続性のチェックリスト

## 変換ラダー / Resolution ladder

| Stage | 表現 | 情報の目安 |
| --- | --- | --- |
| A | Live action | 最高情報量の identity 基準 |
| B | 2D animation | 同一人物・同一デザイン、描画のみ変更 |
| C | High-detail pixel art | 約 64〜96 px |
| D | Low-resolution pixel art | 約 32×48 px |
| E | Extreme low-resolution sprite | 約 16×24 px、最近傍拡大・アンチエイリアスなし |

各段階で表情情報・階調・色数・髪のディテール・衣服の皺・輪郭の複雑さを明示的に減らします。ピクセル風テクスチャを貼るだけの結果にはしません。

## 設置 / Install

Qoder がプロジェクト内で Skill を読み込むパスは `<project>/.qoder/skills/<name>/` です。このリポジトリの正本は `skills/<name>/` に置くので、そこへ写すかリンクします。

```bash
# 1) リポジトリを取得
git clone https://github.com/ozekimasaki/multi-resolution-character-transfer.git

# 2) 対象プロジェクトへコピー（手軽）
cp -r multi-resolution-character-transfer/skills/multi-resolution-character-transfer \
      <your-project>/.qoder/skills/
```

編集しながら使いたい場合は junction で正本を直接参照できます（Windows・管理者権限不要）。

```powershell
New-Item -ItemType Junction `
  -Path "<your-project>\.qoder\skills\multi-resolution-character-transfer" `
  -Target "<clone>\skills\multi-resolution-character-transfer"
```

全プロジェクト共通で使いたい場合は `<project>` の代わりに `~/.qoder/skills/` へ置いてください。

## 使い方 / Usage

```
/multi-resolution-character-transfer
```

自然言語でも起動します。キャラクター画像を添付して「このキャラがモニターに入って、段々ドットが荒くなって、元に戻ってくる30秒のプロンプト作って」と頼む形です。

最小入力はキャラクターの画像または明確な描写です。加えて尺・アスペクト比・移動経路（どの機器を渡るか）・使いたい動画モデル・最後のオチを指定するほど結果が安定します。

## 構成 / Repository layout

```
├── README.md
├── LICENSE                       MIT
├── .gitignore
└── skills/multi-resolution-character-transfer/
    ├── SKILL.md                  本文（ワークフロー手順 1〜9）
    ├── agents/openai.yaml        ChatGPT / Codex 向けのインターフェース定義（他環境は無視可）
    ├── assets/icon.svg           アイコン
    └── references/
        ├── prompt-patterns.md    状態別プロンプトの再利用パターン集
        └── renoise-submission.md 公開例・入出力・品質チェックリスト
```

このリポジトリ自身で Skill を生やすときは、`.qoder/skills/multi-resolution-character-transfer` を `skills/` 側へ junction したものをローカルに置いています（`.qoder/` は追跡外）。

## Notes

- 動画プロンプトの既定モデルは Seedance 2.5（30秒）。他モデルの指定があればその前提に組み替えます。
- 画面文字・字幕・ロゴは原則入れません。音声を切っても内容が伝わる構成にします。
- 大人キャラクターの年齢感は全段階で固定します。

## License

[MIT](LICENSE) です。詳細は LICENSE を参照してください。
