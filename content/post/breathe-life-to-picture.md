---
title: "写真に息を吹き込むビューワー"
date: 2020-11-07T16:19:19+09:00
description: "まるでハリー・○ッター風？写真に息を吹き込むビューワー"
featured: false
draft: false
toc: false
# featureImage: "/images/path/file.jpg"

# menu: main
thumbnail: "/thumbnails/breathe-life-to-picture.jpg"
shareImage: "/thumbnails/breathe-life-to-picture.jpg"
codeMaxLines: 10
codeLineNumbers: false
figurePositionShow: true
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

QAマーカーで囲まれた写真を映すと写真が動き出すビューワーアプリのプロトタイプです。

ある日たまたま出会った Babylon ARの[この記事](https://babylonjs.medium.com/babylon-ar-7823ab4a80c1)を見て、これ使えば映画ハリー・ポッターの中でで出てきた動く写真っぽいものが実現できそう！と思ったので作ってみました。


## デモ

出演: toku345 と 息子の fu
{{< youtube aBELKxVI5oU >}}


## 制作時期

2019年12月 ~ 2020年2月頃


## コード

- https://github.com/toku345/sandbox/tree/master/public/babylonjs
- https://github.com/toku345/sandbox/tree/master/public/opencvjs

## 使用した主な技術

- [babylon.js](https://www.babylonjs.com/)
- [Babylon AR](https://github.com/BabylonJS/BabylonAR)
  - [OpenCV.js](https://docs.opencv.org/master/d5/d10/tutorial_js_root.html) ・・・ Babylon ARの中で使用


## 学んだこと

- Babylon AR は PCのブラウザでしか動作しなかった
  - モバイル端末だとリソース不足なのかも
  - ARKit とか ARCore とか使えば モバイル端末でも動かせるかも（※ 未検証）

- 実際に動作するところを同僚や家族に見せて驚いたり・楽しんでもらえた
  - プロダクトの開発・レビューだと全然苦じゃなかった
  - 苦労しなくてもモチベーションの維持ができた
    - こういうちょっと人をビックリさせたり、楽しんでもらえるプロダクトをこれからも作っていきたいなぁ
