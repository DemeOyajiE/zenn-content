---
title: "[02] Git入門"
emoji: "✨"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [git]
published: true
---

:::details はじめに
こんにちは、ダメおやじエンジニアです。
Zennに初登校できたもののGitで記事公開するまでにいろいろトラブルを経験しました。

そんな自分みたいな人が同じ問題にぶつかった時にスムーズに解決したい。
まあ、何日か経過した自分が一番みるんでしょうけどね(笑)
:::

:::details 変更履歴
2021/3/31   初稿
:::

このページでは、Gitの一連の操作を紹介します。

# 完成予定図




# 画像と画像リンク
#### 画像
```md:画像
![altテキスト](https://画像のURL)
```
![ダメおやじエンジニア](https://storage.googleapis.com/zenn-user-upload/avatar/855b921149.jpeg)

##### 画像の横幅指定
URLの後に半角スペースを空けて` =○○x`と記述すると、画像の幅をpx単位で指定できます。
画像の表示が大きすぎる場合などに便利です。
```md:画像（横幅指定）
![altテキスト](https://画像のURL =100x)
```
![ダメおやじエンジニア](https://storage.googleapis.com/zenn-user-upload/avatar/855b921149.jpeg =100x)


##### キャプション付け
画像のすぐ下の行に`*`で挟んだテキストを配置すると、キャプションのような見た目で表示されます。
```md:画像（キャプション付）
![altテキスト](https://画像のURL)
*キャプション*
```
![ダメおやじエンジニア](https://storage.googleapis.com/zenn-user-upload/avatar/855b921149.jpeg =100x)
*caption*

#### 画像リンク
```md:画像リンク
[![altテキスト](画像のURL)](リンクのURL)
```
最後に、`画像横幅=100x`,`キャプション`,`リンク`を組み合わせて、
画像をクリックするとZennの公式サイトに飛ぶように設定してみました。
[![ダメおやじエンジニア](https://storage.googleapis.com/zenn-user-upload/avatar/855b921149.jpeg =100x)](https://zenn.dev/zenn)
*画像をクリックしてZenn公式サイトへ*

画像リンクはキャプション不要ですね。対応してませんでした。


# テーブル
テーブルの境界として`|`で挟んだテキストを配置します。
ヘッダーとテーブルの境界は`---`を使いましょう。
スペース等は自分で無くても、多くても整形してくれるようです。
```md: table
| Head1 | Head2 | Head3 |
|  ---  | ---   |---|
| text1 | text2 |text3 |
| text4 | text5 | text6     |
```
| Head1 | Head2 | Head3 |
| ---   | ---   | ---   |
| text1 | text2 | text3 |
| text4  | text5  | text6   |


# コードブロック（ファイル名付）
コードは` ``` `で挟むことでブロックとして挿入できます。
言語を指定するとコードへ装飾（シンタックスハイライト）が適用されます。
```
` ``` `python: test.py　※\は表示の都合でつけてますが、実際はありません
print("Hello python")
` ``` `
```
結果はこちら
↓
```python: test.py
print("Hello python")
```




# Zenn独自の記法
Zennでは`メッセージ(message)`と`警告メッセージ(message alert)`を表示することができます

```md:メッセージ
:::message
メッセージをここに
:::
```
:::message
メッセージをここに
:::

```md:警告メッセージ
:::message alert
警告メッセージをここに
:::
```
:::message alert
警告メッセージをここに
:::

:::details　さいごに
マークダウン記法を学べただけでなくZennはとても見やすくレイアウトしてくれる最適な
ツールだなと感じました。

それより、GitにPushするのに苦しんだ～
ここは後で別で解説しよう。

人生はまだまだこれからだ！
:::

#### 参考サイト
@[card](https://zenn.dev/zenn/articles/markdown-guide)

