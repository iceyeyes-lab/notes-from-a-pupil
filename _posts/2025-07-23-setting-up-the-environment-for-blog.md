---
layout: single
title: "ブログ作成のための環境構築"
date: 2025-07-23 18:20:00 +0900
categories: ブログ作成作業
---

## Gitをインストールする

Eclipseでコードを公開したときはEclipse内で完結したが、ブログアップにはGitが必要。

1. 以下でダウンロード&インストールする。

[Gitダウンロードページ]([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. コマンドプロンプトでバージョン確認

`git --version `

→git version 〇〇が表示されたらOK

## GitHubにリポジトリの作成

名前をつけてパブリックで作成する。

名前は URLに入るので、**kebab-case**（小文字とハイフンで単語を区切る形式）で書くこと。

## Jekyllのインストール

JekyllはRubyで記述されているため、Rubyをインストール→Jekyllをインストールする流れ。
細かい方法などは以下参照
[Jekyllについて](https://jitera.com/ja/insights/33597)

## Rubyのインストール

コマンドプロンプトを開いていたらそのまま、閉じてたら開いて以下を入力
「gem install bundler jekyll」
(インストールは数分かかる場合あり)
Successfully installed ほにゃらら、とたくさん出てきたらOKっぽい。
念のための確認で、コマンドプロンプトで以下を実行
`jekyll -v`
→jekyll 4.x.xのように表示されればOK。

## Jekyllでブログを作る

[Rubyインストールサイト](https://rubyinstaller.org/downloads/)
からダウンロードしてインストーラーを実行する。
finishを押すとコマンドプロンプトが開始される(finishの画面でチェックが入っている場合)ので、操作できるようになったらEnterを押す。
MSYS2 baseとMINGW開発ツールチェーンとやらがインストールされる。
最後にまたEnterを押すと消える。

一通りインストールできたら、コマンドプロンプトを開いて「ruby -v」と入力。「ruby 3.x.x ...」と出たらOK。

1. 新しいJekyllブログを作る。
以下のコマンドで、Jekyll用のプロジェクトを作成する。(My-blogというフォルダを作る)
`jekyll new my-blog`
    
    ## Jekyllのセットアップ
    
2. 作成したフォルダに移動する。
以下のコマンドを入力する。
`cd my-blog`
3. サーバーを起動する。
以下のコマンドを入力。
`bundle exec jekyll serve` 
Server running… press ctrl-c to stop.と出たらサーバー起動した状態。
4. ブラウザでブログを見る。
ブラウザを開いて
`http://127.0.0.1:4000/` 
または
`http://localhost:4000/` 
にアクセスする。「Welcome to jekyll!」の画面が出たら成功。

記事のアップロード方法は→（Notionで書いた記事をアップする）参照

```
ChatGPTからの初心者向けおすすめ
既成のテンプレートテーマを使う方法

例：
	•	Minimal Mistakes
	•	Chirpy

これらを Forkして自分のリポジトリにコピーして使うのが簡単とのこと
```