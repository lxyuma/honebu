# 経緯

## 流行

- 以下の流行
 - jQuery => 動きのあるサイト/DOMにEventListenerをbindしまくるソース
 - Ajax => SinglePageApplication

=>複雑化してしまったjsソース

そこで、js上でmoduleを整理していく流れが出てきた。

## FWまで

初めは、自分たちで作っていたが、幾つか共通で使える物がFWとして普及。

Model Viewとそれ以外各FW毎に様々なコンポーネントが準備された事から、

javascript MVC(MV*) framework等と呼ばれるようになった。


# MVCとは

- Model : 
- View:
- Controller:

普段、サーバー側で書いているMVCは、model2と呼ばれる物。

Controllerが中心.

本来は、smalltalk時代に出来たもので、Viewが中心に動く。

jsのMVCも、今のサーバー側のものより、smalltalk自体のMVCに近い。

諸説あるが、今のjs系FWは大きく分けると、MVPと、MVVMに分かれる。

## MVP

Viewが中心に動く

MVVMは、データバインディングがある。

## 参考

- todoMVC
 - http://todomvc.com/
- MVCの経緯
 - http://addyosmani.com/blog/understanding-mvc-and-mvp-for-javascript-and-backbone-developers/
- MVCパターン
 - https://gist.github.com/tily/1362110


# many FW

- 人気の分布
 - http://caliper.io/blog/2013/Javascript-Framework-Popularity/

沢山、frameworkがある。

# いつ、必要になるか？

一般的には、
- 大規模なjs開発
- SinglePageApplication

とされるが、
Backboneの場合、非常に軽量で融通が利くので、普通のWebアプリから適用してOK

# Backboneとは

Ashが開発(underscore.jsやcoffeescriptの作者)

MVPに分類される。

図。

## 事例

事例がとにかく多いのが特徴。

- foursquare
- Airbnb
- LinkedIn
- Groupon Now
- Hulu
- Pinterest

大体、最近出てきたサービスは、殆どBackbone。

- おまけ
 - jsの動きが多くてwebアプリっぽくない感じがしたら、consoleでBackboneと入れてみよう
 - functionが返ってきたらそれは、Backboneを使ってる。

## backboneはなぜ流行ったか？

軽量だから。SPAのみで使う必要ない。

普通のwebアプリでも使える。

## 普通にjquery使って書くのと比べてどうなる？
(普通のwebアプリ)
- Eventの口が整理される。
- リソース系の処理と画面描写の処理が分かれる

結論、ソースが整理される。
=>保守しやすい。次、追加改修し易い。

# これから

周辺技術もふまえながら、Backboneの勉強する。

- Parse:BaaSのパイオニア。facebookに買収され非常に未来のあるクラウドサービス。事例も多い。
- underscore.js:Backboneが依存してるライブラリ。最近、関数型プログラミングの文脈で注目。
- bower/yeoman: client側/server側のライブラリ管理。
- grunt.js:task runner。
- mocha + chai:最近、勢い出てきたtest framework
- marionette.js:backbone上のframework。非常に効率よくbackboneアプリを作れる。

# 最後

Backbone(underscore) + Marionette + bower/yeoman + grunt + mocha/chaiを使って

todoアプリを作ります。

