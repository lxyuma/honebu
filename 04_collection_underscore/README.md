# はじめに

BackboneはjQueryとunderscoreに依存しています。
jQueryは非常に多くの現場で使われているクロスブラウザ用ライブラリのデファクトスタンダードで、特に説明は要らないでしょう。
それと比べてunderscore.jsは、今ひとつ普及していないようです。

http://www.google.co.jp/trends/explore?q=jQuery#q=jQuery%2C%20underscore.js%2C%20Backbone.js&cmpt=q

underscoreはbackbone内部でModel/Collection関係の処理やextend等で使われています。
Backboneのソースを書いていると頻繁にunderscoreを書く事になります。

それでは、これからunderscoreについて少し見てみようと思います。


# underscore.jsとは

Backboneと同じように、Jeremy Ashkenasさんが作ったjavascriptのライブラリです。
公式ページを見ると、多くの関数型プログラミングを提供する為のライブラリであると記載されています。

そもそも、関数型とは何でしょうか？
今日は、この話をしてから、underscore.jsに戻ってこようと思います。

## 関数型プログラミング

## underscoreのソースを解析する

- 関数型の良いお手本

http://underscorejs.org/docs/underscore.html

## components

- Collection(Array or Objects)
- Arrays
- Functions
- Objects
- utility
- Chaining

よく使うものだけ、簡単に見て行きましょう。

## Collection

- each

- map

- reduce

- find

- contains

## Arrays

- first

- rest

- compace

- zip

- range

## Functions

- bind

- bindAll

- once

## Objects

- keys

- values

- pairs

- extend

- defaults

- clone

## Utility

- random

- mixin

- template

## Chaining

- chain

- value


