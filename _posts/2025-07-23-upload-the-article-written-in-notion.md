---
layout: single
title: "Notionで書いた記事をアップする"
date: 2025-07-23 18:15:00 +0900
categories: ブログ作成作業
---

## まずはNotionでの作業

1. アップしたい記事を開く
2. 右上の「…」から「エクスポート」を選択
3. ダウンロードフォルダにzipがあるので展開する

## ファイルそのものに行う作業

1. 記事ファイル名を以下の書き方に変更

`[2025-07-22-hajimete-no-kiji.md](http://2025-07-22-hajimete-no-kiji.md)`

```
年月日、記事タイトルはURLに書かれるので、文字化けを防ぐために、**kebab-case**（小文字とハイフンで単語を区切る形式）で書くこと。
```

1. ブログを作成した場所へファイルを移動する

C:\Users\(ユーザー名)内に作成したブログフォルダ（my-blogなど）の中に**_posts**フォルダがあるので、記事ファイルはその中にファイルを移動する。

（ChatGPTはコピーとしていたが、元の記事はNotion側にあるので、ファイルを無駄に増やさないように移動とした。）

```
画像ファイルは、記事ファイルとは別に**assets/images/**へ入れる必要がある。
ブログフォルダ直下に無い場合は、新たに作成してその中に画像ファイルを入れていくこと。
```

1. 記事の先頭にフロントマターを入れる

移動した記事をメモ帳などで開き、以下を上部に書き込む。

```
---
layout: single
title: "テスト記事"
date: 2025-07-22 12:00:00 +0900
categories: （カテゴリ名1,カテゴリ名2）
tags: （タグ名1,タグ名2,タグ名3）
---
```

このタイミングで記事内を整える。

- \# で書いたタイトルはフロントマターに書かれているものがタイトルとなるので消しておく
- 画像ファイルリンクは以下のように書き換えておくと後でラクになるはず。

`![代替テキスト]({{ site.baseurl }}/assets/images/xxxx.jpg)` 

## コマンドプロンプトでの作業

1. ブログフォルダを開く

`cd C:\Users\(PC上のユーザー名)\my-blog(Jekyllで作成したブログ名)\notes-from-a-pupil(いろいろあって足すことになった部分。任意)`

1. Gitを初期化

`git init`

→Initialized empty Git repository in C:/Users/（ユーザー名）/my-blog/.git/と表示される。

1. GitHubリポジトリをリモートとして追加

`git remote add origin [https://github.com/iceyeyes-lab/notes-from-a-pupil.git](https://github.com/iceyeyes-lab/notes-from-a-pupil.git)`

- URLはGitHubで作成したリポジトリURLに置き換える
- URLの最後に.gitが無くても、入れておくのがおすすめとのこと。
1. リモートが設定できたか確認

`git remote -v`

→ URLが（fetch）と（push）の二つ表示されればOK

1. ファイルをステージング

`git add .`

（全てのファイルをステージ）

1. コミット

`git commit -m "Initial commit"`

Please tell me who you are.とか聞かれたら、以下を実行する

- ユーザー名を設定

`git config --global [user.name](http://user.name/) "iceyeyes-lab"`

"”内はGitHub上のユーザー名を入れる

- メールアドレスを設定

`git config --global user.email "GitHubに登録しているメールアドレス"`

- 設定を確認

`git config --global --list`

1. GitHubにプッシュ

`git push -u origin main`

（mainブランチがないと言われた場合は以下を実行）

```
git branch -M main
git push -u origin main
```

→Connect to GitHubというサインイン画面が出てくる。

## GitHub画面

1. Connect to GitHubでは、ブラウザ、コード、トークンでサインインができる。

手軽なのはブラウザとのことなのでブラウザでサインインする。

1. 無事に進むとコマンドプロンプトに戻りGitHubへのプッシュが完了する。
2. GitHubのブログ用リポジトリを開き、ファイルがちゃんと入っているか確認する。

## GitHub Pagesに公開する

1. リポジトリのSettings→Pagesに移動する
2. 「Branch」のプルダウンを選択。「none」から「main」に変更
3. フォルダは/(root)のままでOK
4. 「Save」で実行
5. 少し時間を置くと、GitHub Pages」設定画面の少し下に以下のような URLが表示される。

`Your site is published at https://ユーザー名.github.io/リポジトリ名/`

### これで公開成功！

## GitHub Pagesでの表示確認

**記事ページで404エラーとなる場合の確認事項**

- 記事ファイルは_postsフォルダ内に入っているか
- ファイル名の形式がyyyy-mm-dd-（kebab-caseで記事タイトル）.mdになっているか
- フロントマターが以下のようになっているか

```
---
layout: post
title: "記事タイトル"
date: YYYY-MM-DD HH:MM:SS +0900
categories: ブログ,水耕栽培,etc...
---
```

- ビルドエラーになっていないか

→ リポジトリの Actions タブ を開いて赤いマークが表示されているとビルドエラー

- _config.yml の baseurlが設定されているか

→url: とbaseurl: の欄を確認し、空で設定されている場合は追加する。

**例:**

```
title: Notes from a pupil
email: your-email@example.com
description: >-
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "/notes-from-a-pupil" # リポジトリ名と同じ
url: "https://iceyeyes-lab.github.io" # GitHub PagesのURL
twitter_username: jekyllrb
github_username: iceyeyes-lab

theme: minima
plugins:
  - jekyll-feed
```

**\ # の所は説明なので消すこと。**

再ビルドされてすぐ開くとまだ反映されていなかったりするので、少し待った方が良い。

**画像が見れない場合の確認**

- 画像の配置場所

→/assets/images/ フォルダ内にあるか。

- Markdown内でのパス指定が正しいか

→記事内の指定は以下のように{{ site.baseurl }} を入れると環境依存のエラーを防げる。

```
![トマトの写真]({{ site.baseurl }}/assets/images/tomato01.jpg)
```