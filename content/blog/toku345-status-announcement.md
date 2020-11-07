---
title: "海馬に優しいプログラマーになるために ~自分の感情を見える化してみた~"
date: 2019-12-11
description: "Classi Advent Calendar 2019 11日目の記事：海馬に優しいプログラマーになるために ~自分の感情を見える化してみた~"
featured: false # Sets if post is a featured post, making appear on the home page side bar.
draft: false # Sets whether to render this page. Draft of true will not be rendered.
toc: false # Controls if a table of contents should be generated for first-level links automatically.
# featureImage: "toku345-status-capture.png"

# menu: main
thumbnail: "thumbnails/toku345-status-capture.gif"
shareImage: "thumbnails/toku345-status-capture.gif"
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
categories:
  - technology
tags:
  - prototyping
  - アドベントカレンダー2019

# comment: false # Disable comment if false.
---

# プロローグ

本記事は [Classi Advent Calendar 2019](https://qiita.com/advent-calendar/2019/classi) 11日目の記事です。

前日の [fusho-takahashi](https://qiita.com/fusho-takahashi)さんの[すごくタメになる記事](https://qiita.com/fusho-takahashi/items/27710fb0a7c9ffd97be6)に続いて11日目は不肖徳光こと [toku345](https://twitter.com/toku345) がお送りします。

昨年に引き続き、今年もお仕事のことは書きません！


# 今年のテーマ

さて、今年は只今チャレンジ中の「自分の感情の見える化」プロジェクトについてお話させていただきます。

最近の自分の「つぶやき」から `感情` を分析し、今のお気持ちやその推移を見える化するプロジェクトです☺️


<a href="https://status.toku345.com">
  <figure>
    <img src="toku345-status-capture.gif" alt="画面イメージGIF" />
    <figcaption style="display: block; text-align: center;">※ 鋭意開発中のため、画面は変更される可能性が多分にあります</figcaption>
  </figure>
</a>

# モチベーション

吉藤オリィさんの[サイボーグ時代](https://www.amazon.co.jp/dp/4866630620) の中で「海馬に優しい人間になれ」という言葉に触発され、「海馬に優しいプログラマー」にならなきゃ😖と強烈に思い始めたのがきっかけ。[^1]

「自分の状態」を見える化するような変なヤツは多くは存在しないでしょうから、初対面の人にもきっと覚えてもらいやすくなり「海馬に優しいプログラマー」に一歩近づけるの間違いなし！！

# 試行錯誤の記録

## 最初は 単純に自分の「ステータス」の見える化してみた

初代は [GitHubのステータスページ](https://www.githubstatus.com/)を参考に、こんな感じの表現にしました。

![初代プロトタイプ](status-prototype-1st.png)


2代目はClassi社におけるフロントエンド・フレームワークのデファクト・スタンダードがAngularなので、Angularの学習も兼ねて作り変えてよりリッチに

![2代目プロトタイプ1](status-prototype-2nd-1.png)

ただ、次第にステータスのパラメータが増えてゆき...

![2代目プロトタイプ2](status-prototype-2nd-2.png)

あばばばば

`「ステータス」の見える化` 期の後半は、（仕事の）やる気が無いこと表明合戦みたいになってしまい、目指したい方向から遠ざかり始めてしまっていました😓

そして、パラメータの設定問題。

この頃は .tsファイルにハードコーディングした値を手動で変更して画面の表示を変えていました。

動的に取得できるようにするために「一日の決まったタイミングでbotとの対話を通してステータスを取得する」ことを検討したのですが、
この数のステータス・パラメータを毎回毎回入力するのが億劫そうなので却下となりました...


## 「感情」の見える化へピボット

という感じで「ステータスの見える化」プロジェクトがあまり面白くなくなってきたため、一時期プロジェクトから離れてしまっていました。

そんなある日。

ふと普段の Slack / Twitter などの投稿内容から判断できたら面白いかも？との啓示が💡

昔調べて[Google Natural Language API](https://cloud.google.com/natural-language/) を使えば文章から感情を分析できることを知っていたので、早速試してみました。

![Google Natural Language APIデモ](google-natural-language-api-demo.png)

**いいじゃーん🙌🏻**

Sentiment の Score を使えば「感情」を数値にでき、その数値を使って感情の状態を表せそうです！


では、これをどう表現するか🤔

最初は、こんな感じでシンプル案を検討しました。

![3代目プロトタイプ](status-prototype-3rd.png)

うーん...

なんかつまんないな

動きのある表現のほうが、より「感情」感を表せそうでいいかも？

ということで、babylon.js を使って実験してみました

![4代目プロトタイプ](status-prototype-4th.gif)

**おっ！いいじゃん、いいじゃん**

あとは、CSS Grid つかって段組して、Chart.jsをつかってグラフを描けば...

ということで、冒頭にお見せした今の形に落ち着きました。


# 作ったものちょこっと紹介

実物は[こちら](https://status.toku345.com/)で触っていただけます。（コードは[こちら](https://github.com/toku345/status)）


「感情」によって3Dイメージが変わります。

`めっちゃハッスルしている時`はこんな感じ⤵︎

![flare](flare.gif)


`普通の時` はこんな感じ⤵︎

![pop large](pop_large.gif)


`疲れ気味の時` はこんな感じ⤵︎

![pop small](pop_small.gif)



`感情の推移` は

こういう「つぶやき」（会社Slackの自分のチャンネルでの投稿）に対して⤵︎

![recent tweets @slack](recent_tweets_slack.png)

こんな感じで推移が見えるようになりました⤵︎

![recent tweets](recent_tweets.png)



 ちょっと長くなってきたので、詳しい技術的な説明は別記事にします🙇🏻‍♂️


# 気づき

## No Good

- 実はまだ「つぶやき」の自動取得できてない💀
- 感情データもファイルで保持しちゃってる...
  - [Cloud FireStore](https://firebase.google.com/docs/firestore)に保存して読み書きできるようにしたかったけど、タイムアウト...😞
- Svelte でどうテスト書くのかを執拗に調べてしまった
  - → 今回の目的はプロダクト品質の作り込みではなく、「感情の見える化」を表現してどうか？なので、テスト書かなくても（まだ）大丈夫なフェーズ
- レスポンシブに対応できてない
- CSS やっぱり苦手なことを再認識した
- 感情の推移グラフx軸が...

- Advent Calendar書く場所をさまよった結果、前日にハッスルして自分ブログ環境を一から用意してしまｓった
  - markdown で書いて、 [Zola](https://github.com/getzola/zola)で static site を生成して、[Firebase Hosting](https://firebase.google.com/docs/hosting) でホスティングしてます
  - だからこの記事しかまだ無いよ🙈


## Good
- なんだかんだ試行錯誤してプロダクトが変わっていくのを後から振り返ってみるの楽しい。
- 最初は他人のために作ってたけど、だんだん自分が楽しくなってきた
- Svelteやったり babylon.jsやったり CSS Grid ちゃんと学んだり...と自分の興味がある技術をストレスフリーで使えるのやっぱ幸せ☺️
- babylon.js は開始時、チュートリアルの必要十分な部分に目を通して、えいやっ！で始めることができた。


# これからやりたいこと

まずは、つぶやきを自動取得にチャレンジします！（[Cloud Functions for Firebase](https://firebase.google.com/docs/functions) 使おうかな）
感情データの保存先は[Cloud FireStore](https://firebase.google.com/docs/firestore)に変更も併せて変更する予定。

将来的には Vision API を使って写真・動画から感情判定した結果も見える化するために使えば、より生の感情に近づけないかなーと。
あと、音声も使って見るもの面白そう。

またAzureも同じようなAPIを公開してるので、その比較もやってみたいですな。

また、Apple Watch とかから、心拍取得したり、マイクで定期的に音声を取得したり、周りの騒音も要素として使えば...


# エピローグ

海馬に優しいプロジェクトのネタは他にもいくつか温めている && 「自分の感情を見える化」プロジェクトでやり残したことを引き続き対応していくので、本ブログを時々覗きに来ていただければ幸いです。

よーし、もっともっと「海馬に優しいプログラマー」になれるようハッスルするぞー💪🏻




明日は [seiga](https://qiita.com/Seiga) さんです！お楽しみに〜

---


[^1]: もちろん「海馬に優しい人間になれ」以外の箇所もすごく興味深く、気付きが多くてわくわくドキドキするので、年末年始にオススメです！
