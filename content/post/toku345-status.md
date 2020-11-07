---
title: "toku345-status（感情の変化を見える化してみよう）"
date: 2020-11-05T14:34:33+09:00
description: "toku345-status: 気分の見える化"
featured: false
draft: false
toc: false
# featureImage: "/thumbnails/toku345-status-capture.gif"

# menu: main
thumbnail: "thumbnails/toku345-status-capture.gif"
shareImage: "thumbnails/toku345-status-capture.gif"
codeMaxLines: 10 # Override global value for how many lines within a code block before auto-collapsing.
codeLineNumbers: false # Override global value for showing of line numbers within code block.
figurePositionShow: true # Override global value for showing the figure label.
categories:
  - technology
series:
  - prototypes
tags:
  - prototyping
  - studying

# comment: false # Disable comment if false.
---

## これは何？

「自分の感情の変化」を可視化できると...

- 自分の感情の変化を客観的に知ることができ、自分自身への理解を深めることができるかも？
- 公開することでチームメイト・同僚に、いつなら話しかけやすいか？などの情報が提供できて、うまく一緒に仕事をするための助けになるかも？

という仮説を（おそらく当時もっていたので）試しに作ってみたプロトタイプです。


Slackへの自分の投稿を Firebase Functions 経由で Google Natural Language API を使って分析し、その結果を Firestore へ格納。発言ごとの分析データをグラフで時系列に表示したり、最新の発言とその一つ前の発言との分析結果の変化によって動く3Dイメージを変えてその瞬間の感情？をビジュアライズしてみました。


（正直に告白すると [2019年のClassi社アドベントカレンダー](https://qiita.com/advent-calendar/2019/classi) の11日目のネタにするために慌てて作りました...😅[^1]）

[^1]: 開発しようと思ったきっかけ、プロトタイプがどう変化してきたかについてはアドベントカレンダーで詳しく書いているので良かったらそちらもご覧ください。[海馬に優しいプログラマーになるために ~自分の感情を見える化してみた~](/blog/toku345-status-announcement)


## 動作イメージ

![デモ](/thumbnails/toku345-status-capture.gif)
※ 現在 status ページは閉鎖中です m(_ _)m

## 制作時期

2019年11月~12月


## コード

https://github.com/toku345/status


## 使用した主な技術

- [Svelte](https://svelte.dev/) v3系
- [babylon.js](https://www.babylonjs.com/)
- [chart.js](https://www.chartjs.org/)
- [Firebase](https://firebase.google.com/)
  - Functions
  - Firestore
  - Hosting
- [Google Natural Language API](https://cloud.google.com/natural-language)


## 失敗したこと

- Svelte のチュートリアルを全部やり終えるまでプロトタイプの製作に 取りかからなかった/ 取りかかれなかった（気持ち的に）。
- Google Natural Language API の分析結果がイマイチで[^2]、おもちゃみたいなグラフしか描けなかった。
- MicrosoftのText Analyticsを試してみたり、Twitterのツイートや他の情報（Apple Watchから生体情報もってくる？）などを使うともっと高精度なものが作れるかもな〜、と妄想だけで終わってしまった。
  - 試作品が動くようになって && アドベントカレンダーの記事を書き終えて 満足してしまいました...

[^2]: 2019年末時点での個人の感想です。今では精度も上がっているかも。

## 学んだこと

- プロトタイプを作るために必要な新技術は、必要十分だけ学ぶようにしたほうが早くプロトタイプを作り始める。
  - → チュートリアルでも基礎のところだけサーッとやってみて、途中で詰まったら調べる作戦をやってみる

- データをより良く使うのは結構苦手だな...ということが改めて認識できた。

---

- Slack上の発言をただそのまま分析して、プロットするだけではだめだったのかもな...
  - 前処理してから分析にかけるとか、各発言の分析結果をプロットするのではなく「いい感じ」(?!)に分析でできるともっとイメージに近いものができあがったかも。
