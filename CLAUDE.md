# movell-site（movell.jp）

離婚準備アプリ movell の公式サイト。GitHub Pages で配信。**main に push すると 1〜2 分で本番公開される**——コミットは慎重に。このリポジトリは public なので、このファイルにも内部事情や秘密情報を書かないこと。

## 構成

- `index.html` — トップ（LP）。ヒーロー実機スライダー / こんな方に / movellでできること（実機付き3ステップ）/ データ保護 / レビュー / 料金 / 生まれた理由 / FAQ / コラム3枠
- `prepare.html` — 離婚準備ガイド（柱記事）
- `articles/` — コラム記事。`articles/index.html` が一覧
- `about.html` / `privacy.html` / `terms.html`
- `css/site.css`（トップ用）/ `css/article.css`(記事用)
- `sitemap.xml` — ページ追加時に必ず更新

## トーンと編集ルール（最重要）

- トーン：**急かさない・煽らない・裁かない**。夜明け前の静けさ
- movell は法律相談サービスではない。断定的な法的助言を書かない。記事には冒頭・末尾に免責を置く
- 記事の制度説明には**公的機関の出典リンク必須**（法務省・裁判所など）。リンクは公開前に `curl` で実在確認（200）
- 運営者の実名・個人的経験の具体的な記述は公開物に載せない
- **アプリに存在しない機能を謳わない**。特に：養育費の計算機能はない（裁判所の算定表へのリンク方式）。スクリーンショット「防止」等の過剰表現もNG（実挙動は「画面録画では内容が映らない」まで）

## アプリの事実（文言を書くときの前提）

- iOS のみ / ¥1,500 買い切り・サブスクなし / アカウント不要・データは端末内のみ / Face ID ロック対応
- 2026年4月施行の民法改正（共同親権）対応
- タブは4つ：整理・記録・知識・まとめ
- App Store ID: `6760285216`

## よくある作業の手順

**新規記事の追加**（`articles/kiroku.html` をテンプレにする）
1. 記事 HTML：JSON-LD（Article / FAQPage / BreadcrumbList）、article-tag、免責×2、source-link、記事中 app-cta、faq-card、まとめ
2. `articles/index.html` の一覧先頭にカード追加
3. `sitemap.xml` に URL 追加（lastmod は当日）
4. 必要ならトップ `#column` の3枠を見直し

**CSS を変更したら** `index.html` の `site.css?v=N` をインクリメント（記事側は `article.css?v=N`）

**実機スクショの差し替え**：`images/screen1〜5-*.png`（1206×2622、iPhone 17 Pro シミュレータ）。同名で置き換えるとヒーローと機能セクションの両方に反映される。タブバーが4タブ（整理・記録・知識・まとめ）の現行版か確認すること

**評価（★）の更新**：トップの `#reviews` の section-desc と、head 内 JSON-LD の `aggregateRating` の **2箇所を同期**させる

**OGP**：`images/ogp.png`（1200×630）。変更しても LINE/X はキャッシュを持つ（送信済みメッセージは永久に古いまま、新規共有も約1週間キャッシュ）。確認は `?v=2` などを付けた URL で
