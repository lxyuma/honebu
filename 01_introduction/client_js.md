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

ここからMVCの経緯を振り返る。

## なぜMVCの知識が必要か？

その前に、なぜこんな事を知る必要があるのか？

Backbone自体、厳密にMV*を定義していない。

今、自分が書いているのがどれなのか？処理をどこに委譲すべきか？考えないといけない。MV*の知識はこれらの判断材料になる。

逆に知らないと、新しいスパゲティが出来る。


## UIの登場

70年代にGUIが登場。

プレゼンテーション層とドメインロジック層が出来た。


## MVC in smalltalk80

- View
    - UIの受け口
    - Controllerを呼び出す
- Controller
    - Modelを操作
- Model
    - EventをFire!

## serverside MVC(model2)

- Controller
    - requestの受け取り
    - responseをHTTPとして返す
    - Modelを操作
    ーViewにdataを渡して描写

- 普段サーバー側FWで書いているのが、これ。

## MVP

- 2つの特徴
    - passive view: viewは素朴に。表示やロジックはPに
    - 監督者としてのController:主にViewがロジックも内包。難しい時にPresenterが処理を引き継ぐ

- View
    - UIの受け口
    - Presenterを呼び出す
- Presenter
    - Modelを操作
    - Viewを更新
- Model
    - PresenterをFire!

## MVVM

- MVPとほぼ同じ(PresenterがViewModel)
    - 違い：ViewModelの変化がデータバインディングによりViewに繁栄

## jsのMV*

jsのMVCも、今のサーバー側のもの(model2)より、smalltalk自体のMVCに近い。

諸説あるが、今のjs系FWは大きく分けると、その多くがMVPと、MVVMに分かれる。(例外ある。また、人によって捉え方も異なる)

BackboneはMVP。(人に寄っては元のMVCという人もいれば、MV*と言う人もいる)


# jsのMV*とサーバー側のMV*

- よくある勘違い：jsのMV* frameworkあるから、サーバー側のMVC要らない？

    - NO
    - 勿論、必要。いつも通りサーバー側も実装。
    - 今迄サーバー側のMVCでまかなっていて、Vが膨らんだので、これを分解してclient側でMVCで整理しようというのが、Backbone

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
    - http://www.google.co.jp/trends/explore?q=Backbone.js#q=Backbone.js%2C%20Angular.js%2C%20Spine.js%2C%20Ember.js%2C%20Ext%20JS&cmpt=q

沢山、frameworkがある。

特に、GoogleTrendsに注目。大体、そんな感じ。

- senchaのExtJsは、昔からUIを売ってて、途中からMVCを付けた(2011年4月)それ以前のデータはあまり関係がない。勢いは衰えてる。
- Backboneが、ここ、2,3年のトレンド
- Angularが去年からすごい勢いで上昇中。
- Ember.jsもそこそこ人気
- Spine.jsはもう？knockout.jsも低い状況。

# いつ、必要になるか？

一般的には、
- 大規模なjs開発
- SinglePageApplication

とされるが、
Backboneの場合、非常に軽量で融通が利くので、普通のWebアプリから適用してOK

むしろ、普通のアプリで書くと、js整理されて、かなりメンテし易くなる。

# Backboneとは

Jeremy Ashkenas(@jashkenas)が開発(underscore.jsやcoffeescriptの作者)

MVPに分類される。


## 事例

事例がとにかく多いのが特徴。しかも、有名なサービスばかり。

- foursquare
- Airbnb
- LinkedIn
- Groupon Now
- Hulu
- Pinterest
- SoundCloud

大体、最近出てきたサービスは、殆どBackbone。

- おまけ
 - jsの動きが多くてwebアプリっぽくない感じがしたら、consoleでBackboneと入れてみよう
 - functionが返ってきたらそれは、Backboneを使ってる。

## backboneはなぜ流行ったか？

軽量だから。SPAのみで使う必要ない。

普通のwebアプリでも使える。

## 普通にjquery使って書くのと比べてどうなる？

- (普通のwebアプリ)
    - Eventの口が整理される。
    - リソース系の処理と画面描写の処理が分かれる

結論、ソースが整理される。
=>保守しやすい。次、追加改修し易い。

## ちなみに、これからどうなる？

誰にも分からないが、最近、angularの勢いが激しい。

- 昔：Backboneと有象無象のFW
- 今：Backboneとangularと有象無象...

angularはpolymerと統合される可能性があるので、

webcomponentの普及と同時にangular勢の時代が来るかもしれない。

これは、だれにも分からないが、とりあえず、今分かる範囲ではBackboneで大丈夫。

※事例の数や情報量は圧倒的にBackboneが多い。

# これから

以下の周辺技術もふまえながら、Backboneの勉強する。

- Parse:BaaSのパイオニア。facebookに買収され非常に未来のあるクラウドサービス。事例も多い。ちなみに、最近日本でもBaaS熱くなってきた。
- underscore.js:Backboneが依存してるライブラリ。最近、関数型プログラミングの文脈で注目。
- bower/yeoman: client側/server側のライブラリ管理。
- grunt.js:task runner。
- mocha + chai:最近、勢い出てきたtest framework
- marionette.js:backbone上のframework。非常に効率よくbackboneアプリを作れる。

# 最後

Backbone(underscore) + Marionette + bower/yeoman + grunt + mocha/chaiを使って

todoアプリを作ります。

