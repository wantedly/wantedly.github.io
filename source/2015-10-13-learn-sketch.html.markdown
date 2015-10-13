---
title: Sketch速習集会
date: 2015-10-13 16:30 JST
tags: Sketch, UI, Web, Design
wantedly_id: 92979
twitter_id: Ui_Pb
github_id: usa619
---

デザイナーの宇佐美 [@Ui_Pb](https://twitter.com/ui_pb) です。

## 速習会とは
2015年10月1日に、 Wantedly のオフィスにてSketch速習会を開催しました！
実は、過去にも何度か社外の方を数名招待する形で速習会を行っております。
なぜ数名のみ紹介する形をとっているかというと、以前から定期的に行っていた社内勉強会に社外の人も数名招待しよう！という流れから速習会を定期開催するようになったからです。そのため、社外の方々だけでなく社内のエンジニアやデザイナーも毎回参加しています。

### 過去に行った速習会
- [JSONScheme速習会](http://wantedly.connpass.com/event/17532/)
- [きれいなCSS速習会](http://wantedly.connpass.com/event/18018/)
- [UML速習会](http://wantedly.connpass.com/event/20077/)
- [データ解析ツール速習会 TreasuData/DOMO編](http://wantedly.connpass.com/event/19585/)
- [Docker速習会](http://wantedly.connpass.com/event/19067/)

### 今回やったこと
今回の速習会では、Sketchファイルの基本的な編集方法とSketchファイルを貰った時に意識して見て欲しいポイントを伝えることを目的に行いました。
Wantedlyではエンジニア、デザイナーともにSketchという共通のツールを使うことで、デザイナーとエンジニア間のコミュニケーションコストを下げよう！という取り組みを行っていることからこのテーマを選んだためです。

速習会中は、デザイナーでない方々にも多くご参加いただいたので、Sketchを「どう使っているか」を実際に見ていただき、
参加していた方々ご自身に実践していただくことで使い方を知ってもらうよう意識してSketchについての発表と実践する機会を設けさせていただきました！

![](images/2015-10-13/1.png)


## 簡単に自己紹介すると
今年の3月まで高校に通っていて、6月からWantedlyにインターンとしてジョイン。9月からデザイナーとして社員になりました。WantedlyではWeb、iOSのUIデザインをメインにやっていて、フロントエンドも書きます。最近はRailsも書くようになりました。個人ではグラフィックアニメーションや写真、DTPなど幅広くやっています。

## こんなこと話しました
デザインツールを使ったことのないエンジニアが多かったので、アートボードの作り方から解説をしました。基本的には導入を丁寧にやってある程度からはトライアンドエラーの繰り返しがツールをの使い道を身につけるにはいいと思っています。なので、スライドでは基礎の操作方法の解説が終わったら難しめの課題を出して、試行錯誤をしてSketchを使ってもらう形になっています。使い方の特徴としては実装するところに重点を置いて、Sketchファイルを作っていくところです。時間的な問題で載せられなかったことがたくさんあるので、またいつかここに書きたいと思います。

<iframe src="//www.slideshare.net/slideshow/embed_code/key/a2iQt2At1xbaiQ" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/core619/sketchwantedly" title="Sketch速習会@Wantedly" target="_blank">Sketch速習会@Wantedly</a> </strong> from <strong><a href="//www.slideshare.net/core619" target="_blank">Ryo Usami</a></strong> </div>

## プラグイン
Sketchを使って高速にデザインを作るにはプラグインが不可欠です。僕が普段使っているプラグインの一部を紹介します。詳しい操作方法は各プラグインのページを参照してください。

#### [Align Text Baseline](https://github.com/soutaro/align-text-baseline-sketch-plugin)
Sketchでは日本語のフォントボディーの解釈にバグがあり、`line-height`が使い物になりません。またその影響で、`Text`のheightが正確な値になっていないため、要素内で垂直中央揃えが効きません。このプラグインはその問題を解決するために作られたもので、ボタンなどを作る時に重宝します。

#### [Content-generator-sketch-plugin-master](https://github.com/timuric/Content-generator-sketch-plugin)
Sketchで作った要素に人名、画像などをまとめて流し込めるプラグインです。Wantedlyでは各募集でイメージ画像を大きく掲載しているので、そこのイメージを再現するのに事前に何枚か募集の画像をダウンロードしておいて自動で流し込めるようにしています。

#### [Sketch Palettes](https://github.com/andrewfiorillo/sketch-palettes)
SketchにはカラーパレットがSketchアプリ全体に紐づけられている`Global Colors`とファイルごとに設定する`Documents Colors`があります。Sketch自体のテンプレート機能を使って`Documents Colors`で頑張ることもできますが、何かと不便な時もあるので、プロジェクトごとにカラーパレットを書き出しておいて、使うときにimportすることにしています。

#### [Sketch Measure](https://github.com/utom/sketch-measure)
width, height, mergin, padding, font-size,colorなど実装の際に確認するパラペーターを可視化することができます。相手がsketchを持ってない場合や実装する人に細かく指示したい場合などに使います。

#### [Wantedly Color Picker](https://github.com/usa619/wantedly-color-picker)
WantedlyではSassでCSSを書いていて、カラーパレットの変数名で色指定を行っています。実装するときにカラーコードから変数名を調べるのがめんどくさかったので、自動で変数名を取得するプラグインを作りました！

##その他

### 懇親会
今回は、焼きそばや唐揚げ、ピザなどの軽食を準備させて頂きました！
社外の方々と話す貴重な機会となり、速習会に参加した社内エンジニアも楽しめました。
ご参加いただいた皆様に感謝です！

![](images/2015-10-13/4.jpg)


### 最後に
Wantedlyでは引き続き、2週間に1度のペースで速習会を行っています。Connpassにて開催の1週間前から募集を開始しております。
今後も、様々なテーマの速習会を開催していく予定ですので、ご興味のある方は是非ご応募ください！
<br>ref [ConnpassのWantedlyグループ](http://wantedly.connpass.com/)
