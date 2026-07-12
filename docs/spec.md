# なうこ LP 仕様書

## 概要

| 項目 | 内容 |
|------|------|
| 対象者 | なうこ（AI VTuber） |
| ファイル | `nauko_lp.html` + `style.css` |
| 目的 | 自己紹介・ポートフォリオ |
| 公開形式 | HTML + CSS の2ファイル構成（外部依存: Google Fonts のみ） |

---

## コンセプト

**「NOW LOADING... — 生成AIの今を届けるVTuber」**

ブルー系パレット（ネイビー・シアン・水色）を基調に、VTuber感とポップかわいい雰囲気を両立させたデザイン。キャラクター画像を Hero に2カラムで配置し、CSS-only パーティクルやアニメーションで動きを演出。技術的な親しみやすさとライブ配信の「今」感を表現する。

---

## ページ構成

| セクション | 役割 |
|-----------|------|
| Header | 固定ナビ。名前 + タグライン |
| Hero | キャラ画像（左）＋ テキスト（右）の2カラム。猫耳SVG / 名前 / タグライン / #毎日なうこ |
| Profile | ON AIRバッジ + 自己紹介リード文 + 詳細テキスト |
| Topics | 発信テーマ4分野（2列グリッド） |
| Gallery | キャラクター画像ギャラリー（3列グリッド、ワイドアイテム対応） |
| CTA | YouTubeチャンネル誘導ボタン + Xアカウントリンク（`@nowko_chan`） |
| Footer | コピーライト + ハッシュタグ |

セクション間は `ribbon-divider`（ピンク/ラベンダーグラデーション + ♡アイコン）で区切る。

---

## カラーパレット

| 変数名 | HEX / 値 | 用途 |
|--------|----------|------|
| `--navy` | `#1a3a6e` | 見出しテキスト・アクセント |
| `--navy-deep` | `#d0e8fa` | Hero・CTA背景（ライトブルー） |
| `--cyan` | `#4dd9f0` | 猫耳グロー・スキャンライン |
| `--cyan-glow` | `#00bfe0` | セクションラベル・ヘッダータグ |
| `--red` | `#c0392b` | （リボン由来・現在未使用） |
| `--paper` | `#f7f7f5` | ページ背景 |
| `--paper-tint` | `#eeecea` | — |
| `--ink` | `#1a1f2e` | 本文テキスト |
| `--ink-soft` | `#5a6070` | サブテキスト |
| `--ink-faint` | `#a8adb8` | 薄いテキスト（topic-desc等） |
| `--line` | `#dcdde0` | — |
| `--pink` | `#4f8eff` | アクセントブルー（ボタン・番号・ドット等） |
| `--pink-soft` | `rgba(79,142,255,0.18)` | ホバーオーバーレイ |
| `--pink-glow` | `rgba(79,142,255,0.45)` | グロー効果 |
| `--lavender` | `#a8cfff` | 薄いブルー・パーティクル |
| `--lavender-soft` | `rgba(168,207,255,0.18)` | ホバーオーバーレイ |
| `--lavender-glow` | `rgba(168,207,255,0.45)` | グロー効果 |
| `--amber` | `#f2a541` | なうこの瞳の色。ハッシュタグ・Topics番号・ON AIRドット・猫耳の目・ポートレートリングに使用 |
| `--amber-glow` | `rgba(242,165,65,0.5)` | ポートレートリング背後のグロー（pink-glowと混色） |
| `--char-size` | `min(340px, 82vw)` | キャラ画像サイズ（モバイルは `min(260px, 70vw)`） |

---

## タイポグラフィ

| 用途 | フォント | ウェイト |
|------|----------|---------|
| 見出し・Hero名前・CTAボタン | Zen Maru Gothic | 400 / 500 / 700 |
| リード文・本文 | Noto Sans JP | 300 / 400 / 500 |
| UI・ラベル・コード系 | Space Mono | 400 / 700 |

---

## アニメーション

| 名前 | 効果 | 対象 |
|------|------|------|
| `fadeUp` | フェードイン + 上昇 | Hero各要素（遅延付き） |
| `glowPulse` | テキストグロー点滅（シアン） | char-glow-ring の bloom |
| `glowPulsePink` | テキストグロー点滅（シアン+ブルー混合） | hero-name |
| `earGlow` | drop-shadow点滅 | 猫耳SVG |
| `scanline` | 横線が上から下へ流れる | Hero背景 |
| `blink` | カーソル点滅 | `_` カーソル / ON AIRドット |
| `floatChar` | ふわふわ浮遊（-1deg ↔ 1deg, 14px 上昇） | キャラ画像 |
| `popIn` | バウンシー登場 | キャラ画像（初回のみ） |
| `twinkle` | きらめき（拡縮 + 回転） | ★ パーティクル / section-label の ♡ |
| `floatHeart` | ♡・★ が下から上昇してフェードアウト | hero-particles |
| `ribbonWave` | グラデーション左右ゆらぎ | ribbon-line / CTA トップアクセント |
| Scroll reveal | IntersectionObserver でフェードイン | `.reveal` クラス要素 |

---

## Hero 構造

```
.hero
  .hero-scanline           // スキャンライン
  .hero-particles          // CSS-only パーティクル（♡×5, ★×5）
  .hero-inner              // 2カラム flex-row ラッパー
    .hero-char             // 左：キャラ画像エリア
      .char-glow-ring      // conic-gradient リング + floatChar + popIn
        img.char-img       // images/nauko.png
    .hero-text             // 右：テキストエリア
      .hero-ears           // 猫耳 SVG
      .hero-loading        // "NOW LOADING_"
      h1.hero-name         // "なうこ"
      .hero-tagline        // サブタイトル
      .hero-hashtag        // "#毎日なうこ"
  .hero-scroll             // "scroll ↓"
```

---

## レスポンシブ

| ブレークポイント | 変更内容 |
|----------------|---------|
| `≤ 768px` | hero-inner を縦積み（col）、テキスト中央揃え、`--char-size: min(260px, 70vw)`、gallery-grid を 2列、wide アイテムは span 1 |
| `≤ 600px` | header padding 縮小、topics-grid を 1列、gallery-grid を 1列、footer を縦積み |

---

## 画像ファイル

| パス | 用途 |
|------|------|
| `images/nauko.png` | Hero キャラクター画像 |
| `images/nauko_stream.png` | Gallery ワイドアイテム（ストリーム） |
| `images/nauko_happy.png` | Gallery アイテム |
| `images/nauko_expressions.png` | Gallery アイテム（表情パック） |
| `images/nauko_comic.png` | Gallery アイテム |
| `images/nauko_design.png` | Gallery ワイドアイテム（キャラデザイン） |

画像が存在しない場合でもレイアウトは崩れない設計。

---

## 未設定・要確認事項（TODO）

- [ ] YouTubeチャンネルURL（現在 `https://www.youtube.com/@nauko` の仮置き）
- [x] X（Twitter）リンクを追加 — CTAセクションに `https://x.com/nowko_chan` へのリンクを設置（`.cta-socials` / `.social-link`）
- [x] OGP設定（SNSシェア用サムネイル・description）— `nauko_stream.png` をアイキャッチに使用。ホスティング後は `og:image` / `twitter:image` を絶対URLに変更すること
- [ ] ホスティング先（GitHub Pages / Netlify / その他）
- [ ] Google Analytics / アクセス解析を入れるか

---

## 変更履歴

| 日付 | 内容 |
|------|------|
| 2026-03-15 | 初版作成。シンプル・ミニマル方針でHTML生成 |
| 2026-03-15 | なうこのVTuberビジュアルに合わせカラー・コンテンツ全面改訂 |
| 2026-03-15 | ポップかわいい系にリデザイン。Hero 2カラム化、Gallery セクション追加、style.css 分離、パーティクル・リボン等追加。仕様書をコード実装に合わせ更新 |
| 2026-03-15 | SVGファビコン追加（`favicon.svg`）、OGP / Twitter Card メタタグ追加（アイキャッチ: `nauko_stream.png`） |
| 2026-07-12 | CTAセクションにXアカウント（`https://x.com/nowko_chan`）へのリンクを追加 |
| 2026-07-12 | なうこの瞳の色（amber, `#f2a541`）を差し色として追加。構成・レイアウトは変えず、ハッシュタグ・Topics番号・ON AIRドット・猫耳の目・ポートレートリングに配色 |
