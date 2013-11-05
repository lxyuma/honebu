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

# 関数型プログラミング

https://docs.google.com/presentation/d/1KTQAH-OK8NDTWtYA6kvNXGF2jmTywD_mhXixN1hXz88/edit?usp=sharing

# underscoreのソースを解析する

- 関数型の良いお手本

http://underscorejs.org/docs/underscore.html

# components

- Collection(Array or Objects)
- Arrays
- Functions
- Objects
- utility
- Chaining

ライブラリなので、基本逆引きで覚えていけば良いのですが、

よく使うものだけ、簡単に見て行きましょう。

# 基本的な書き方

underscoreは"_."を使う。

- each

eachが基本。ループ文。

```
_.each(配列, iterator関数)

```

- iterator関数の引数
  1. 要素
  1. index
  1. 元の配列


```
languages = ["ruby", "javascript", "node.js"];

_.each(languages, function(element, index, list) {
  console.log(index + ":" + element + " < in " + list + ">");
});
```

元々ある関数を使う事もできる

```
_.each([1, 2, 3], alert);
//=> alerts each number in turn...
```

このalertを自分の関数にしても良い。(=関数型っぽくなってきた)

# Collection(Object & Array)

以下、公式pageより。

- map

全ての配列に同じ操作をする。

```
_.map([1, 2, 3], function(num){ return num * 3; });
// => [3, 6, 9]
```

- reduce

合計値を作る

```
var sum = _.reduce([1, 2, 3], function(memo, num){ return memo + num; }, 0);
// => 6
```

- filter

条件に合う値のみを取得する

```
var evens = _.filter([1, 2, 3, 4, 5, 6], function(num){ return num % 2 == 0; });
// => [2, 4, 6]
```


# Functions

- bind

関数にobjectをbindする。

```
_.bind(関数, bindしたいobject, 関数に与える引数)
```

関数内では、thisが、bindしたいobjectになる。

このbindしたいonjectにthisそのものを指定する事がよくある。

```
var func = function(greeting){ return greeting + ': ' + this.name };
func = _.bind(func, {name: 'moe'}, 'hi');
func();
// => 'hi: moe'
```

- bindAll

複数のメソッドにobjectをbindする。

```
_.bindAll(object, *methodNames)
```

第２引数は可長変。複数のメソッドを指定できる。

bindの複数版。こっちの方がよく見る。

```
var buttonView = {
  label  : 'underscore',
  onClick: function(){ alert('clicked: ' + this.label); },
  onHover: function(){ console.log('hovering: ' + this.label); }
};

_.bindAll(buttonView, 'onClick', 'onHover');

// When the button is clicked, this.label will have the correct value.

jQuery('#underscore_button').bind('click', buttonView.onClick);
```

Backboneでよくinitialize内でmodel/collectionとbindしたeventとthisを結ぶために使う。


# Objects

- extend

プロパティのコピー。

```
_.extend(destination, *sources)
```

オブジェクトxにオブジェクトyの値を入れる。

```
x = {a: "1", b: "2"};
y = {b: "3", c: "4"};
z = _.extend(x, y);

console.log(z)
// Object {a: "1", b: "3", c: "4"}
```

まあ、予想通りの結果ですが、この時、元のx,yを見てみると、

```
console.log(x)
// Object {a: "1", b: "3", c: "4"}

console.log(y)
// Object {b: "3", c: "4"}
```

xも変わってるので注意。

(extendはxのshallow copyに対して操作している)

# Backbone * underscore.js

Backboneの中でunderscoreめっちゃ使われてる

- classのextendや、cid等基本的な機能
- Modelでunderscoreから委譲
- Collectionでunderscoreから委譲

特にCollectionでunderscoreから委譲されたメソッドを非常によく使う。

```
ex)
collection.each(function (item) { ... })
```

関数型っぽい記述が活かせるのも、Collection周りの処理。

# 実際のFP in js(Backbone)

やや複雑なロジックになった時に思い出そう。

なんか例示する予定だったけど、間に合わなかったので、誰かのブログを。

http://victorsavkin.com/post/63551894251/functional-refactoring-in-javascript


