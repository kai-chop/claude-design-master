# claude-design-master

**Claude fable-5 が公開版の監査・整備・完成を担ったSkill** — 高評価デザインSkillとの競合分析・梱包・検証をモデル自身が主導しました。

[English README](./README.md)

[Claude Code](https://claude.com/claude-code) 用のWebデザインSkill — **国内の厳選デザインギャラリー**の掲載水準を狙うためのワークフローです。

多くのデザインSkillはモデルに「美しくして」と言うだけ。このSkillは感覚語を**数値・判断手順・反証ラウンド**に置き換え、それを通過するまで「完成」と呼ばせません。

## 汎用デザインSkillとの違い

| 特徴 | claude-design-master |
|---|---|
| **定量的な完成判定** | Q1〜Q10の10項目チェック。コントラスト比は目視でなく**実際に計算**する |
| **反証ラウンド** | 完成宣言の前に、逆ジャンル検査・削除検査・ブラーテスト・1画面1主役テストを実行し、修正点をユーザーに報告してから完成とする |
| **トークンファースト** | トークン定義前のCSS禁止: OKLCH等差階調・90-7-3則・モジュラースケール・4px基底余白スケール。実装での生HEX/生px禁止 |
| **ジャンルレシピ** | cool/コーポレート/LP等6種の変数レシピを**最初に1つ選び、混ぜない** |
| **日本語組版** | 行間・字間・ジャンプ率などCJKテキストの組版指針を収録（英語圏Skillにはほぼ存在しない） |
| **優先順位の明文化** | 衝突時は 視認性・アクセシビリティ > 視覚階層 > ジャンルらしさ > 装飾。モデルに「雰囲気」でなく判定基準を与える |

## 収録内容

```
SKILL.md                      Phase 0〜5ワークフロー・レビューモード・優先順位
knowledge/
├── 01-color.md               OKLCH設計・90-7-3則・コントラスト基準
├── 02-typography.md          モジュラースケール・ジャンプ率・日本語組版
├── 03-layout-space.md        余白スケール・グリッド・比率
├── 04-hierarchy-gaze.md      視線誘導・ゲシュタルト・認知法則
├── 05-motion.md              duration/easing数値・実装優先順位
├── 06-genres.md              ジャンル別変数レシピ（cool/corporate/LP等）
└── 07-evaluation.md          定量チェック・反証ラウンド・スコアリング
```

ナレッジは該当フェーズでのみ読み込むprogressive disclosure設計で、トークン負荷は最小です。

## インストール

**個人用（全プロジェクトで有効）:**

```bash
git clone https://github.com/kai-chop/claude-design-master ~/.claude/skills/design-master
```

**プロジェクト単位:**

```bash
git clone https://github.com/kai-chop/claude-design-master .claude/skills/design-master
```

あとは普通に依頼するだけ——「デザインして」「かっこよくして」「見やすくして」「デザインレビューして」で発動します。

## ワークフロー概観

- **Phase 0** ジャンル判定 — 形容詞3つ・ターゲット・最重要アクション1つを言語化し、レシピを1つ選ぶ
- **Phase 1** トークン設計 — 色・タイポ・余白・角丸・罫線・影をCSS変数で先に定義
- **Phase 2** 構造 — 重要度スコア1-5（スコア1は1画面に1つ）・余白の階層・視線誘導
- **Phase 3** 実装 — セマンティックHTML・トークン参照のみ・clamp()レスポンシブ
- **Phase 4** モーション — ホバー150ms → スクロール出現 → ヒーロー。easeOutExpo既定・prefers-reduced-motion必須
- **Phase 5** 反証と完成判定 — 定量Q1-Q10・ブラーテスト・反証ラウンド（省略禁止）

## ライセンス

[Apache License 2.0](./LICENSE)
