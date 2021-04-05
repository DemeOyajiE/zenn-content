---
title: "[02] Git入門(1/3) GitHubリポジトリをZennに連携させる"
emoji: "✨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [git,zenn]
published: true
---

:::details 変更履歴
2021/3/31   初稿
:::

# はじめに

:::details Gitを学ぶきっかけ（ZennでのGitHub連携）
私は、Zennで技術記事を投稿したいと思い、**Zennのコンテンツ作成ガイド** を見て投稿方法を学ぼうと思いました。
@[card](https://zenn.dev/zenn/articles/editor-guide)

作成ガイドを見ていくと、投稿方法には2種類あることが分かりました。
1. Web エディター
2. ローカルのテキストエディター + CLI（GitHub連携)

Webエディターの方が今の自分には合ってるけど、ドラフト記事の状態で編集するのはスマートじゃないなあ。元に戻すの面倒だし、、やっぱローカル環境で作業確認してから投稿すべきだろうなあ<br>

周りのヤングなエンジニアみてると`Gitでバージョン管理するのが普通っしょ`みたいな雰囲気。。

**よし！　これを機にGitを学んで、オッサンもエンジニアの会話に入れてもらおう！** 
という思いから`２．ローカルのテキストエディター + CLI（GitHub連携)`を選択しました。

<br>
でも、、、投稿するまでの道のりは簡単では無かった(ToT)　私にとってはですが、、、
:::

**これから3回わたってGitHubを連携させてZennに記事を投稿する手順を説明します**
あくまで私のやり方なので、もっと良い方法があれば教えて頂けると嬉しいです。

> **概略図**
![概略](https://storage.googleapis.com/zenn-user-upload/6s5tsw9uhiqktp6tc1lb369u5vj1)
> 1. GitHub登録とZennへの連携
>   1.1 GitHub登録
>   1.2 Zennへの連携
> 2. ローカル環境構築(Zenn CLI,Gitのインストール) 
> 3. Gitコマンドによる投稿手順(add,commit,remote,push)


> Zennの投稿には興味無いんだよね～、またGit環境も構築済みなんだよね～ 

という方は、`3.Gitの投稿までのコマンド実行手順`だけご覧下さいませ。
:::message
`2.ローカル環境構築(Zenn CLI,Gitのインストール) `
`3.Gitの投稿までのコマンド実行手順`
は、準備中です。今しばらくお待ちください。
:::



<br>

# 1. GitHub登録とZennへの連携
#### やりたいこと
まずはGitHubサイトで自分のリポジトリを作成し、そのリポジトリをZennに連携する作業を行います。

:::details リポジトリって何？の方はこちら
リポジトリ(repository)とは、ファイルやディレクトリの状態を記録する場所のことです。
単純に言えば、自分の作業場（作業記録）を作ると思えばいいでしょう。

■参考：サル先生のGit入門
https://backlog.com/ja/git-tutorial/intro/02/

:::


![1. GitHub登録とZennへの連携](https://storage.googleapis.com/zenn-user-upload/ul7ujyg03rpz5i30nuw2gs6satwi)
*1.1 GitHub登録 → 1.2 Zennへの連携*

## 1.1 GitHub登録
まずは、GitHubにアクセスして、`GitHubに登録する`をクリックしましょう。
> GitHub公式サイト https://github.co.jp/

![1.1 GitHub登録-1GitHubサイト](https://storage.googleapis.com/zenn-user-upload/8vt9lch3gptalpr4n4nz9h62r84g)

すると、アカウント登録画面が出てくるので
`Username`, `Email`, `Password`などの必要な情報を入力して`Create Account`をクリックしましょう。
![1.1 GitHub登録-2アカウント登録](https://storage.googleapis.com/zenn-user-upload/sl0vo55wtluiarsgzino34vxlfya)

Welcome to GitHubなどの画面で、主にどんな仕事してますか？と質問が来るけど、どれでもOK
（例： Software Engineer)
登録したメールアドレスで認証すればOK。


#### 次にリポジトリの登録です  
私は、下記の3つを記載して`Create repository`をクリックして作成しました。
* Reposigtory name : zenn-content 
* Description      : Zenn連携用のリポジトリです (Optional)
* Public / Private : Public

![1.1 GitHub登録-3リポジトリ作成](https://storage.googleapis.com/zenn-user-upload/o5i2b5dy4hqfzqkewoycx5itgc1w)

#### リポジトリが完成しました。
![1.1 GitHub登録-完了](https://storage.googleapis.com/zenn-user-upload/hj7p8la84zmeaqrwa1gujt7880gs)

:::message alert
リポジトリには、Password、クラウドリソースのIDなどはおかないようにしましょう。
仮想通貨のマイニング処理などに悪用されて多額請求されることもあるらしい
特に埋め込みコードに要注意。
:::

## 1.2 Zennへの連携
では、1.1で作成したリポジトリをZennのダッシュボードと連携してみましょう。
#### まずは、Zennダッシュボードサイトにアクセスして下さい
> Zennのダッシュボード https://zenn.dev/dashboard/deploys

#### そして`リポジトリを連携`をクリックしてください。
![1.2 Zennへの連携-1連携クリック](https://storage.googleapis.com/zenn-user-upload/53ap1m83tsgvqiplytma88f6em0p)

#### 次に1.1で作成したリポジトリを選択して連携しましょう。
ローカル環境で投稿を事前確認するZenn CLIもインストールして下さいね。

> **手順は以下の通り**
>1. Only select repositories を選択
>2. Select repositoriesのプルダウンから1.1で作成したリポジトリを選択
>3. Install & Authrize をクリック
![1.2 Zennへの連携-2リポジトリの選択](https://storage.googleapis.com/zenn-user-upload/xp0kr27uzmwqy3q500v9dqs47yvt)


#### GitHubリポジトリをZennへ連携することができました。
![1.2 Zennへの連携-3完了](https://storage.googleapis.com/zenn-user-upload/7aqhjuw03iopkgne9kpzixlv9huk)
<br>

参考サイト　https://techacademy.jp/magazine/6235


<br>



:::details さいごに
技術記事を書くのって楽じゃないですね。早く下記の記事を投稿したいです。もう少しお待ちください。
2. ローカル環境構築(Zenn CLI,Gitのインストール) 
3. Gitコマンドによる投稿手順(add,commit,remote,push)
:::



#### 参考サイト
[git公式サイト(Book)](https://git-scm.com/book/ja)
@[card](https://zenn.dev/zenn/articles/markdown-guide)

