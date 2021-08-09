---
title: "[02] Git入門 GitHubリポジトリをZennに連携させる【前編：環境構築】"
emoji: "✨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [git,zenn]
published: true
---

:::details 変更履歴
2021/3/31   初稿
2021/4/12   タイトル、記事を2部構成に大幅変更（前編：環境構築、後編：Git入門）
2021/8/9    Gitインストールは後編に変更
:::

# はじめに

:::details Gitを学ぶきっかけ
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

**これから2回わたってGitHubを連携させてZennに記事を投稿する手順を説明します**
自己流なので、もっと良い方法があれば教えて頂けると嬉しいです。

**【前編：環境構築】**
　　1. インターネット公開用の環境構築（GitHub登録とZennへの連携）
　　2. ローカル環境構築(Zenn CLIのインストール)

**【後編：記事投稿(Git)】**
　　3. Gitインストール
　　4. Gitコマンドによる投稿手順(add,commit,remote,push)
<br>
![概要図](https://storage.googleapis.com/zenn-user-upload/918f4992b1f2f63474d247d4.png)
*概要図*

> Zennの投稿には興味無いんだよね～、またGit環境も構築済みなんだよね～ 

という方は、`【後編：記事投稿(Git)】`にスキップして下さい。


# 1. GitHub登録とZennへの連携
早速、GitHubサイトで自分のリポジトリを作成し、そのリポジトリをZennに連携する作業を行いましょう。

:::details リポジトリって何？の方はこちら
リポジトリ(repository)とは、ファイルやディレクトリの状態を記録する場所のことです。
単純に言えば、自分の作業場（作業記録）を作ると思えばいいでしょう。

■参考：サル先生のGit入門
https://backlog.com/ja/git-tutorial/intro/02/

:::


![1. GitHub登録とZennへの連携](https://storage.googleapis.com/zenn-user-upload/ul7ujyg03rpz5i30nuw2gs6satwi)
*1.1 GitHub登録 → 1.2 Zennへの連携*

## 1.1 GitHub登録
GitHubにアクセスして、`GitHubに登録する`をクリックしましょう。
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
#### Zennダッシュボードサイトにアクセスして下さい
> Zennのダッシュボード https://zenn.dev/dashboard/deploys

#### `リポジトリを連携`をクリックしてください。
![1.2 Zennへの連携-1連携クリック](https://storage.googleapis.com/zenn-user-upload/53ap1m83tsgvqiplytma88f6em0p)

#### 1.1で作成したリポジトリを選択して連携しましょう。

手順は以下の通り
>1. Only select repositories を選択
>2. Select repositoriesのプルダウンから1.1で作成したリポジトリを選択
>3. Install & Authrize をクリック
![1.2 Zennへの連携-2リポジトリの選択](https://storage.googleapis.com/zenn-user-upload/xp0kr27uzmwqy3q500v9dqs47yvt)


## Github-Zenn連携が完成！！
やりました！　これであなたの記事を投稿する場所ができました(^o^)/~ 
Githubに投稿すればZenn上で記事が見えるようになりましたよ。
![1.2 Zennへの連携-3完了](https://storage.googleapis.com/zenn-user-upload/7aqhjuw03iopkgne9kpzixlv9huk)
<br>


でも、
書きかけの記事は途中で公開したくないあ。。。
自分のPC上で記事の事前チェックしたいなあ。。
と思いますよね。

`2. ローカル環境構築(Zenn CLIインストール)`で自分PC上で確認できるZennローカル環境構築の仕方について説明します。


# 2. ローカル環境構築(Zenn CLIインストール)


![2-01-ローカル環境構築](https://storage.googleapis.com/zenn-user-upload/7bedb3cd7b7c8a31d163ffa4.png)


## 2.1 Zenn CLI (Node.js) インストール
まずは、Zenn CLIというツールをインストールしましょう。
インストールすると、編集中の記事ファイル（hello-zenn-world.md)をChromeなどのブラウザで`http://localhost:8000`と入力するだけで、Zennサイト投稿のプレビュー画面を確認できるようになります。

**Node.jsのインストール確認**
Zenn CLIはNode.js製のアプリケーションだそうです。
自分のPCにNode.js環境がインストールされているかコマンドプロンプトで確認しましょう。

```
$ node --version
```
バージョンが出てきたらOKです。
![Node.jsのバージョン確認](https://storage.googleapis.com/zenn-user-upload/aff51681dc39ed893bd74555.png)

:::details Node.jsをインストールしていない方へ
Zenn CLIはNode.jsという言語で作成されているため、Node.jsもあらかじめインストールするしないとだめらしいっす。
下記サイトからインストールしましょ。
https://nodejs.org/ja/download/

ちなみに私は 2021/3/9 に推奨版の14.16.0 LTS　をインストールしました。
:::
<br>

**Zenn CLIのインストール**
コマンドプロンプト上でZenn投稿用の作業フォルダーに移動して、下記コマンドを実行してください

```
$ npm init --yes            # プロジェクトをデフォルト設定で初期化
$ npm install zenn-cli      # zenn-cliをインストール
```
npm initの実行結果
![init実行](https://storage.googleapis.com/zenn-user-upload/8e72110c26a1cea219f70c2a.png)

npm installの実行結果
![install実行](https://storage.googleapis.com/zenn-user-upload/ac41084851dca1b8a7ffa5ef.png)



## 2.2 ZennCLI初期設定
2.1の作業フォルダー上で、Zennの初期設定コマンドを実行してください。

```
$ npx zenn init      # Zennの初期設定
```
これで記事、本を格納するための必要なファイルができあがります。

`README.md`や.`gitignore`のほか、`articles`と`books`という名前のフォルダーが作成されます。この中に投稿用のマークダウンファイル`（◯◯.md）`を入れていくことになります。

実行結果はこんな感じ
![zenn初期化](https://storage.googleapis.com/zenn-user-upload/105223a5f046e3f6e6cb2eb6.png)

<br>


## 2.3 Zenn Preview画面の起動

下記コマンドでPreview画面を起動します。
```
$ npx zenn preview      
```

**ブラウザで動作確認**
Chromeなどのブラウザで下記を入力してください
```
http://localhost:8000/
```
## おめでとうございます！
ローカル環境作業は終了しました。
下記画像のようにZenn Editorの画面が表示されていたらOKです。
![最終確認](https://storage.googleapis.com/zenn-user-upload/85acd58afa1a56760be6c828.png)

---
## 次回以降のZenn Editor起動
作業フォルダーで`2.3 Zenn Preview画面の起動`を行えばZennCLIで事前確認ができます。


## 最後に
ZennCLIはとても便利、投稿記事のマークダウンファイル(xxx.md)をVS Code上で保存すれば
即時にその結果が確認できるからです。みなさまも是非トライしてみてください。

次回は、いよいよ投稿記事作成からGitを使って記事投稿するまでの手順を説明します。

:::details さいごに
技術記事を書くのって楽じゃないですね。早く下記の記事を投稿したいです。
後編を夏休み中にアップしますのでもう少しお待ちください。
:::



#### 参考サイト
* [Zennのコンテンツ作成ガイド](https://zenn.dev/zenn/articles/editor-guide)
* [サル先生のGit入門](https://backlog.com/ja/git-tutorial/intro/02/)
* [今さら聞けない！GitHubの使い方【超初心者向け](https://techacademy.jp/magazine/6235)
* [git公式サイト(Book)](https://git-scm.com/book/ja)

