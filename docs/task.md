# なうこ LP 改善タスク

## 概要

現状の なうこLP に対する改善タスク一覧。過去のリデザイン作業（ポップかわいい系への全面改訂、Xリンク追加、amber差し色追加など）はコミット履歴と `docs/spec.md` の変更履歴を参照。

---

## タスク一覧

### 1. コンテンツ確定（ユーザー作業） — 優先度: 高
- [ ] YouTubeチャンネルの実URLを確認・差し替え（現在 `https://www.youtube.com/@` は仮置き）
- [ ] X以外のSNS（Instagram / TikTok 等）のリンクを追加するか判断

---

### 2. パフォーマンス — 優先度: 高
- [ ] キャラクター画像6枚（合計約11.4MB、1枚あたり1.6〜2.2MB）を圧縮・WebP化してファイルサイズを削減
- [ ] Hero以外（Gallery内）の `<img>` に `loading="lazy"` を付与
- [ ] Hero画像（`nauko.png`）は初期表示に必要なため、優先読み込み（`fetchpriority="high"`）を検討

---

### 3. SEO — 優先度: 中
- [ ] `<meta name="description">` を追加（現在 `og:description` / `twitter:description` のみで、検索結果に使われる通常のメタディスクリプションが無い）
- [ ] `robots.txt` / `sitemap.xml` の設置を検討

---

### 4. Favicon整理 — 優先度: 低
- [ ] `favicon.svg` がリポジトリに存在するが、実際は `<link rel="icon">` で `nauko.png` を直接参照しており未使用。SVGを `type="image/svg+xml"` として使うか、不要なら削除するか整理する

---

### 5. アクセシビリティ — 優先度: 中
- [ ] `.btn-yt` / `.header-name` 等のリンクでキーボードフォーカス時の視認可能なアウトラインがあるか確認
- [ ] `prefers-reduced-motion` への対応（現在、猫耳グローや文字グロー等のアニメーションが常時ループしており未対応）

---

### 6. アクセス解析 — 優先度: 低
- [ ] Google Analytics / Plausible 等の解析タグを導入するか判断

---

### 7. ドキュメント整合性 — 優先度: 低
- [ ] `docs/spec.md` のTODOで「ホスティング先」が未チェックのままだが、実際はGitHub Pagesで運用中のため反映する

---

## 検証チェックリスト（各タスク実施後）

- [ ] Lighthouse等でパフォーマンス / SEOスコアを確認
- [ ] モバイル実機でスクロール・画像表示を確認
- [ ] `git push origin main` 後、GitHub Pagesへの反映を確認
