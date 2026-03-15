# なうこ LP リデザイン タスクリスト

## 概要
`nauko_lp.html` をポップかわいい系にリデザインし、キャラクター画像をHeroに追加する。

---

## タスク一覧

### [ ] 1. 画像ファイルの準備（ユーザー作業）
- [ ] `nauko.png` を `/Users/hiroshi/0315/` に配置（ストリーミングシーン推奨）
- [ ] `nauko_expressions.png` を `/Users/hiroshi/0315/` に配置（任意）

---

### [x] 2. Google Fonts 追加
- [x] `<link>` タグに `Zen+Maru+Gothic:wght@400;500;700` を追加

---

### [x] 3. CSS変数追加（`:root`）
- [x] `--pink: #ff6fa8`
- [x] `--pink-soft: rgba(255,111,168,0.18)`
- [x] `--pink-glow: rgba(255,111,168,0.45)`
- [x] `--lavender: #c9b8ff`
- [x] `--lavender-soft: rgba(201,184,255,0.18)`
- [x] `--lavender-glow: rgba(201,184,255,0.45)`
- [x] `--char-size: min(340px, 82vw)`

---

### [x] 4. 新アニメーション追加
- [x] `@keyframes floatChar` — キャラ画像のふわふわ浮遊
- [x] `@keyframes twinkle` — 星パーティクルのきらめき
- [x] `@keyframes floatHeart` — ハートパーティクルの上昇
- [x] `@keyframes popIn` — キャラ画像のバウンシー登場
- [x] `@keyframes ribbonWave` — リボン区切り線のゆらぎ
- [x] `@keyframes glowPulsePink` — ピンク+シアン混合グロー（hero-name用）

---

### [x] 5. Hero HTML 構造変更（2カラムレイアウト）
- [x] `.hero-particles` — CSS-onlyパーティクル（♡5個 + ★5個）
- [x] `.hero-inner` — 2カラムラッパー（flex-row）
- [x] `.hero-char` + `.char-glow-ring` + `.char-img` — キャラ画像エリア
- [x] `.hero-text` — 既存テキストのラッパー化

---

### [x] 6. キャラクター画像スタイル
- [x] `.char-glow-ring`: conic-gradient（pink→cyan→lavender）ボーダー
- [x] `popIn` + `floatChar` アニメーション適用
- [x] `.char-glow-ring::before`: ブルームグロー
- [x] `.char-glow-ring::after`: ダークリング（画像とグラデの間の区切り）
- [x] `.char-img`: 円形クリッピング

---

### [x] 7. パーティクルシステム（CSS only）
- [x] `.hero-particles` コンテナ
- [x] `.particle` 基本スタイル（`--x`, `--d`, `--s` カスタムプロパティ）
- [x] `.particle.heart::before` — ♡ ピンク
- [x] `.particle.star::before` — ★ ラベンダー

---

### [x] 8. ヘッダー変更
- [x] `.header-name`: Zen Maru Gothic、ホバーグラデーションテキスト
- [x] `.header-tag`: シアン→ピンク グラデーションテキスト
- [x] `header border-bottom`: ピンクtint

---

### [x] 9. Hero テキスト変更
- [x] `.hero-name`: Zen Maru Gothic + `glowPulsePink`
- [x] `.hero-tagline`: Zen Maru Gothic + ラベンダー色
- [x] `.hero-hashtag`: ピンク色
- [x] 猫耳SVG: 耳先ドット→ピンク、ストローク→グラデーション

---

### [x] 10. Profile セクション変更
- [x] `.profile-badge`: ピル形状、ピンク色、ラベンダーボーダー
- [x] `.about-lead strong::after`: ピンク→ラベンダーグラデーション
- [x] `.section-label::before`: ♡ 装飾追加

---

### [x] 11. Topics カード変更
- [x] `.topics-grid`: gap 16px、transparent背景、ボーダー廃止
- [x] `.topic-item`: border-radius 20px、ラベンダーボーダー、バウンシーホバー
- [x] `.topic-item::before`: 全面ブラッシュオーバーレイ
- [x] `.topic-num`: ピンク色
- [x] `.topic-title`: Zen Maru Gothic

---

### [x] 12. リボン区切り線
- [x] HTML: `<div class="ribbon-divider">` に置換
- [x] CSS: グラデーションライン + ♡ アイコン + ribbonWave アニメ

---

### [x] 13. CTA セクション変更
- [x] `.cta-section::after`: rainbow ribbon トップアクセント
- [x] `.cta-heading`: Zen Maru Gothic
- [x] `.cta-eyebrow`: ピンク色
- [x] `.btn-yt`: ピル型、ピンク→ラベンダー fill on hover

---

### [x] 14. フッター変更
- [x] `border-top`: ピンクtint
- [x] `footer span:first-child::before`: ♡ 装飾

---

### [x] 15. レスポンシブ対応
- [x] `@media (max-width: 768px)`: hero-inner を縦積み、テキスト中央揃え
- [x] `--char-size` をモバイル向けに縮小

---

## 検証チェックリスト

- [ ] ブラウザで `nauko_lp.html` を開く
- [ ] Hero: キャラ画像（左）＋テキスト（右）の2カラム表示
- [ ] キャラ画像: グラデーションリング + ふわふわ浮遊アニメ
- [ ] ♡・★ パーティクルが下から上に流れる
- [ ] Topicsカードが丸く、ホバーで浮き上がり＋ピンクブラッシュ
- [ ] リボン区切り線がピンク/ラベンダーグラデーション
- [ ] モバイル（768px以下）でキャラ上・テキスト下の縦積み
- [ ] `nauko.png` がなくても画面が壊れない
