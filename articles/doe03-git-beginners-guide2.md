---
title: "Git入門 GitHubリポジトリをZennに連携させる【後編：記事投稿(Git)】"
emoji: "✨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [git,zenn]
published: true
---

:::details 変更履歴
2021/8/9   初稿
:::

:::details Githubの登録がまだの方
[[02]Git入門 GitHubリポジトリをZennに連携させる【前編：環境構築](https://zenn.dev/dameoyajie/articles/doe02-git-beginners-guide)で環境のセットアップをお願いします。
:::


# はじめに
いよいよ`後編：記事投稿(Git)`です。
**VS Code上で投稿記事作成して、Githubに記事投稿するまでの手順を説明します。**

**【前編：環境構築】**
　　1. インターネット公開用の環境構築（GitHub登録とZennへの連携）
　　2. ローカル環境構築(Zenn CLIのインストール)

**【後編：記事投稿(Git)】**
　　3. Gitインストール
　　4. Gitコマンドによる投稿手順(add,commit,remote,push)
![概要図](https://storage.googleapis.com/zenn-user-upload/918f4992b1f2f63474d247d4.png)
*概要図*


# 3. Gitインストール
下記サイトからGitをダウンロードしてインストールしましょう。
その際にDefault EditorをVS Codeに設定します。
https://gitforwindows.org/

![Gitダウンロード](https://storage.googleapis.com/zenn-user-upload/bef75bfe78f5ff85bd995c73.png)

Default Editorは、最初Vimになっていますのでここで`VS Code`に変更しましょう。
VimでOKの方は作業不要です。
![VS Codeをデフォルトエディターに設定](https://storage.googleapis.com/zenn-user-upload/a8234db3a5783bdc456791e1.png)

#### Zennでブランチ名を master 以外に設定している方(例:main)

下記ように、Zennで連携したブランチ名`main`を入力して下さい。
ブランチ名が`master`の方は作業不要です。

![ブランチをmainに変更](https://storage.googleapis.com/zenn-user-upload/731a5c8e2cdc841748237679.png)

ちなみに私は、mainブランチ名を設定しています。mainの方が馴染みがあるからかな。。
![zennでmainブランチ名を設定](https://storage.googleapis.com/zenn-user-upload/8bd20c7c5c478991da696f78.png)

これでGitのインストールできました。

#### Gitインストールの確認
まずは、VS Codeを起動してGitがインストールされているか確認しましょう。

> 1.「ターミナル」から`新しいターミナル`を起動　
> 2. ターミナルでGitのバージョン確認
```
$ git --version
```
![Git version](https://storage.googleapis.com/zenn-user-upload/cd568ecf378ca9ad0d53d9e6.png)


# 4. Gitコマンドによる投稿手順(add,commit,push)
いよいよ投稿手順ですね。手順はこんな感じですね。
![投稿手順の概要図](https://storage.googleapis.com/zenn-user-upload/500ba49816027347a8fdc77b.png)

## Zennの投稿用記事を作成
Zenn用の作業フォルダーに移動し、`npx zenn new`コマンドで記事を作成してください。
> $ npx zenn new:article --slug <ファイル名> --title <記事のタイトル> --type <tech or idea>
> 
> ファイル名：hello-zenn-world ※小文字の半角英数とハイフン(-)の組み合わせで12～50文字
> タイトル　: Hello zenn world　※任意
> タイプ　　：tech              ※techは技術記事、ideaはアイデア記事

:::message alert
誰かが一度登録したファイル名だと登録できないようです。
今回、私は`hello-zenn-world`　から　　`hello-zenn-world-202108091346`　にファイル名を変更してPublishしました。
:::
![](https://storage.googleapis.com/zenn-user-upload/9a6c70c44413152c5e17bc7a.png)

```
$ npx zenn new:article --slug hello-zenn-world-202108091346 --title Hello zenn world --type tech
```
テスト記事が出来ました。
![テスト記事](https://storage.googleapis.com/zenn-user-upload/86439891420c70f7a6f52fc7.png)

投稿用にちょっとファイルを編集しましょう。
```md: hello-zenn-world-202108091346.md (変更前)
title: "Hello"
emoji: "📌"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: []
published: false

```
(変更内容)
- topic に zennを設定
- pubulished変更：false -> true
- 本文を追加


```md: hello-zenn-world-202108091346.md (変更後)
title: "Hello"
emoji: "👻"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [zenn]
published: true

# Hello zenn world !
Zennへの投稿テストページです。
```



## 4.1 git add(working ⇒ staging)
> 1.変更管理アイコン（左側の丸が三つで線でつながったアイコン）をクリック
> 2.対象ファイルの右のプラス（＋）ボタンをクリック
![git add](https://storage.googleapis.com/zenn-user-upload/4cb5bb23b45a83151e323052.png)


## 4.2 git commit
これでStagingへファイルが登録されました。
![git add finish](https://storage.googleapis.com/zenn-user-upload/7c6417ee06afcd7266f18f84.png)

次にローカルリポジトリに登録するためにコミットメッセージを入力しましょう。


## 4.3 git push
↑矢印が1になっているのでクリックしてPushしましょう。
![git push](https://storage.googleapis.com/zenn-user-upload/025d8ee7a85e5de0484cd917.png)

## 完成です。お疲れ様でした。
![完成](https://storage.googleapis.com/zenn-user-upload/8afc11c25bec58e3f37f97bd.png)


<br>
テストで投稿した記事はいらないのでGithubから削除しましょう。
Zennだけ削除してもGithubからの再同期で復活してしまいますよ(ToT)



## さいごに
これから学んだことを少しずつでもZennで投稿して行ければと思います。



#### 参考サイト
* [サルでも分かるGit入門の前に！Git使い方高速入門編<<動画>>](https://www.youtube.com/watch?v=i1L3A0SLDyg&t=24s)
* [Visual Studio Code入門 #07：Gitクライアントはもういらない！ VSCodeで、Gitを使いこなそう<<動画>>](https://www.youtube.com/watch?v=vMZ0C06soxA)
* [Gitの各領域(working directory,staging area,repo)とコマンドの関係図](https://khid.net/2020/05/git-working-directory-staging-area-repo-command/)

