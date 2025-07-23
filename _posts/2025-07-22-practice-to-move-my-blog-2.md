---
layout: single
title: "GitHubにブログを引っ越しさせるための練習②"
date: 2025-07-22 11:40:00 +0900
tags: markdown, github, blog
categories: ブログ作成作業
---

# GitHubにブログを引っ越しさせるための練習②

## Notionで書いた記事をJekyllで編集する

ここからはPCで作業する。

```
Jekyllで編集し、GitHubにプッシュするには
GitHubにブログ用リポジトリ作成やJekyllのインストールが必要
方法については以下
[ブログ作成のための環境構築]
```

1. Notionで書いた記事を.mdファイルとしてコピペして保存する。

 `[2025-7-14-markdown-tips.md](http://2025-7-14-markdown-tips.md)`

　すると、以下のように表示される。

　[2025-7-14-markdown-tips.md](http://2025-7-14-markdown-tips.md)

1. Jekyllブログの_postsフォルダに1で保存した記事を追加する

　　記事の先頭には「フロントマター」と呼ばれるメタ情報を書く

```
---
layout: post
title: "Markdownの使い方"
date: 2025-07-13
tags: [markdown, github, blog]
categories: [開発]
---

（ここから本文をそのままコピペ）
```

1. リポジトリの「Settings」→「Pages」→「Source」で main ブランチ + / (root) または /docs を選べば公開される。
