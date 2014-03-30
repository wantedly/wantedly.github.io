---
title: AngularJSを導入することと、恋のときめきと一歩踏み出す苦しみと。
date: 2014-03-24
wantedly_id: 14000
facebook_id: imai.takayuki
twitter_id: imaimiami
github_id: imaimiami
---

#### 春です。

こんにちは、春ですね。

いつから春なんだっけと思って、近くの人に聞いてみたら「花粉が飛んだら春」だそうです。
来てますね、春。

春には花粉以外にも、「ときめき」が飛び交います。
朝のあの子の挨拶だったり、最近通い始めたスタバの店員さんの笑顔、そして、
Angular.jsのUIバインディングのスマートさにときめきます。

![ios_image](images/2014-03-24/angular.gif)

「あの子と話せたらハッピーだろうな」、「うちのサイトのDOMもバリバリ動かしたらカッコいいだろうな」
とか春の陽気はポジティブな妄想を誘います。
ただ、その妄想を現実に落としこむは簡単なことではなく、冬までに降り積もったシガラミが邪魔をします。
中学時代に奇跡的にもらったラブレター、押入れに密かにしまわれているトレーディングカード、
そして、jQueryで書かれたコードだったりが邪魔します。でも、変わらなくちゃ手に入れられないものもあります。

#### AngularJSを導入する

AngularJSを導入するにあたって、
まっさらな状態からの構築なら良いのですが、既存のサービスに導入となると戸惑います。
自分も最初はjQueryとぶつかって難しいよねとか思ってました。

でも、意外とそうでもないです。


例えば、あなたのサイトで使われまくっている`cool-select`という超coolなパーツがあったとして、

JS

``` js
$(function(){
  $(".cool-select").on("change", function(){
    alert("Cool!");
  });
});
```

HTML

```html
<li ng-repeat="tool in tools" class="animate">
  <span>{{tool.name}}</span>
  <select class="cool-select">
    <option value="">どのくらい好き？</option>
    <option value="normal">いや、普通に</option>
    <option value="straw">ストローで飲むくらい好き</option>
  </select>
</li>
```
実装のされ方にもよると思いますが、この`ng-repeat`の中で使用しているonChangeイベントはbindされません。
ブラウザすら`Cool!`と言ってくれません。悲しい。

こういう場合はDirectiveとして取り込んであげればいいと思います。

JS

```js
ToolApp.directive('coolSelect', function() {
  return {
    restrict: 'A',
    link: function postLink(scope, element, attrs) {
      element.on("change", function(){
        alert(attrs.bigSelect);
      });
    }
  };
});
```

`restrict: 'A'`は属性指定です。`big-select`という属性のある要素を指すことになります。
`link`は`ng-repeat`のイテレーションのたびに呼び出されます。  

AngularJSはjQueryが読み込まれいる場合、`angular.element`からjQueryのfunctionを呼び出せます。
なのでjQueryの時のコードと同じように`.on`でbindしてます。

[AngularJS: API: angular.element](http://docs.angularjs.org/api/ng/function/angular.element)

HTML

```html
<li ng-repeat="tool in tools" class="animate">
  <span>{{tool.name}}</span>
  <select big-select="Nice" ng-model="tool.like">
    <option value="">どのくらい好き？</option>
    <option value="normal">いや、普通に</option>
    <option value="straw">ストローで飲むくらい好き</option>
  </select>
</li>
```

これで`onChange`イベントをbindすることが出来ました。
おまけで`cool-select`に値を渡せるようにしています。

#### 補足  
今回使用したコードはすべて以下にあります。動くと思います。

[https://gist.github.com/imaimiami/9722407](https://gist.github.com/imaimiami/9722407)

AngularJS入門は結局公式が良かったです。良い記事があれば教えてください。

[AngularJS: Tutorial: Tutorial](http://docs.angularjs.org/tutorial)

また、冒頭のGIF画像は、チームの生産性のためならばどんなチャレンジもいとわない
[同僚](/2014/03/27/setup-elasticsearch-cluster-on-ec2-with-chef.html)に敬意を表したものです。

以上、また会いましょう！
