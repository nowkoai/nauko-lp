# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

AI VTuber **なうこ** のランディングページ。GitHub Pages でホスティング。
URL: `https://nowkoai.github.io/nauko-lp/`

## ファイル構成

- `index.html` — GitHub Pages で配信される本番ファイル（`nauko_lp.html` と常に同期する）
- `nauko_lp.html` — 作業用コピー
- `style.css` — 全スタイル（ビルド不要、素のCSS）
- `favicon.svg` — SVGファビコン
- `images/` — キャラクター画像（`nauko.png`, `nauko_stream.png`, `nauko_happy.png`, `nauko_expressions.png`, `nauko_comic.png`, `nauko_design.png`）
- `docs/spec.md` — デザイン仕様書（コード変更時は合わせて更新する）
- `docs/task.md` — タスク管理ドキュメント

## 行動指針

ユーザーの入力が曖昧な場合は AskUserQuestion ツールを積極的に使ってください。

## 重要なルール

**`index.html` が本番ファイル。** `nauko_lp.html` を編集した場合は `index.html` にも同じ変更を反映する。

**OGP画像URLは絶対URLにする。** `https://nowkoai.github.io/nauko-lp/images/...` の形式で指定。相対パスではSNS・iMessageのプレビューで画像が表示されない。

**ビルド不要。** HTMLファイルをブラウザで直接開いてプレビュー可能。`main` ブランチにプッシュすると自動デプロイされる。

## デザインシステム

カラーは `style.css` の `:root` にCSS変数で定義。変数名に注意：`--pink`（`#4f8eff`）や `--lavender`（`#a8cfff`）は実際にはブルー系の色。主要フォント：**Zen Maru Gothic**（見出し・UI）、**Noto Sans JP**（本文）、**Space Mono**（ラベル・コード系）。

## デプロイ

```bash
git add index.html nauko_lp.html  # （その他変更ファイルも追加）
git commit -m "..."
git push origin main
```

`main` ブランチのルートから配信。プッシュ後1〜2分で反映される。
