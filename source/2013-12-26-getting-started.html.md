---
title: 新人エンジニアに読んで欲しい英語ドキュメントまとめ (Ruby/Rails編)
date: 2013-12-26
wantedly_id: 10599
facebook_id: yoshinori.kawasaki
---

こんにちは！エンジニアの[川崎](https://www.wantedly.com/users/10599)です。

嬉しいことに、Wantedly開発チームの仲間は2013年の1年間で2倍に増えました。2013の最初には自分、 [awakia](https://www.wantedly.com/users/15382) と [reikubonaga](https://www.wantedly.com/users/9306) の3人でしたが、
デザイナなのにXCodeも使いこなす [ferasyahin](https://www.wantedly.com/users/42889)、
Chef使いのプロダクティビティ・エンジニア [spesnova](https://www.wantedly.com/users/323185)、それからこのブログのデザインもやってくれたエンジニア [imaimiami](https://www.wantedly.com/users/14000) の加入で合計6人になりました。最近ではさらに [kento](https://www.wantedly.com/users/2217896) や [shin-en](https://www.wantedly.com/users/300507) がインターンとして活躍してくれています。

Wantedlyに入社してくるエンジニアは、なぜかRubyもRailsもやったことのない人ばかりなので(自分もそうでした)、
今日はそんな彼ら新人のために、Ruby/Railsで開発をするときに役立つページをまとめてみました。

初めてRails開発をする人に参考にして欲しいと思います。


## チュートリアル

[Ruby on Rails Tutorial: Learn Web Development with Rails](http://ruby.railstutorial.org/)

まず、全くRailsをやったことがない場合は適当なチュートリアルをひと通りやるのがオススメです。
有名なのはRails Tutorialです。3.2系と4.0系の両方対応していて、最近では有志によって[日本語翻訳](http://railstutorial.jp/)も公開されました。git入門やHerokuへのdeployも少しだけカバーしているので、これをやっておくとWantedlyでの開発フローにスムーズに参加出来ます。



## Rails Guides & APIs

[Ruby on Rails Guides](http://guides.rubyonrails.org/)

少しRailsの基本を理解したら、公式のRails Guidesをさっと眺めておくとよいでしょう。
トピック毎に基本＋αの情報が調度良い分量でよくまとまっています。最初は全部目を通せなくてもどんなトピックがあるのかだけは知っておくと、後々の開発で振り返りやすいです。ちなみに、`master`ブランチの[Edge Guides](http://edgeguides.rubyonrails.org/)も存在します。


[Ruby on Rails API](http://api.rubyonrails.org/)

公式のRails APIページも良く出来ています。メソッド名でインクリメンタルサーチができるので、個人的にはこれを愛用しています。


[Rails Style Guide](https://github.com/bbatsov/rails-style-guide)

コミュニティによって作られたRailsのベスト・プラクティス集としてRails Style Guideがあります。
必ずしも完璧に従う必要はないですが、良いとされている書き方を知っておくことは役に立つでしょう。


## Ruby

[Ruby 2.1.0 Core API](http://ruby-doc.org/core-2.1.0/) / [Ruby 2.0.0 Core API](http://ruby-doc.org/core-2.0.0/)

Rubyのリファレンスとしてはruby-doc.orgのものを個人的には参照しています。こちらもクラス名やメソッド名でインクリメンタルサーチができます。`Array`, `Hash`, `Enumerable`, `String`クラスあたりは見ておくと幸せになれると思います。メタプログラミングに興味があれば`Class`, `Module`, `Kernel`, `Object`, `BasicObject`クラスあたりも見ておくとよいでしょう。

[Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide)

Rails Style Guideと同様に、コミュニティによって作成されたRubyのStyle Guideです。



## RSpec

[RSpec - Relish](https://www.relishapp.com/rspec)

Wantedlyでは自動テストのフレームワークにRSpecを使っています。
Railsでの開発に慣れてきたら、RSpecについても時間をとって学習しておきましょう。
テストを書くことに対して感じる精神的なハードルを下げておかないと、
自動テストの重要性を頭で理解していても、
面倒臭がってテストを書かなくなってしまいます。

自動テスト重要。


[Better Specs](http://betterspecs.org/)

RSpecのベスト・プラクティス集です。BADな書き方とGOODな書き方の実例がしっかり書いてあって実践的。



## 最後に


Railsはバージョンアップ毎の変化がかなり大きいフレームワークです。2013-12-26現在の最新は4.0系で、現在は時期バージョンの4.1.0 betaが公開されてます。Wantedlyでは3.2系を使っているので、ドキュメントやブログなどを読んで調べ物をするときに、どのバージョンが対象なのか、いつ頃の記事なのかを注意してみておかないと、バージョン間の非互換性に悩まされることになるので注意です。体感的には2012年より前の文章は参考にしないほうがいいと思ってます。




---
#### 追伸

Wantedlyでは新オフィスで、毎週木曜18:00〜もくもく会を実施しています。[ご興味ある方はこちらからご参加ください :)](https://www.wantedly.com/projects/5106)
