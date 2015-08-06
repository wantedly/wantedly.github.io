---
title: Hashicorp Product Meetup というイベントを開きました
date: 2015-08-06 10:17 JST
tags: vagrant, packer, serf, consul, terraform, vault, atlas, hashicorp
wantedly_id: 323185
twitter_id: spesnova
github_id: spesnova
---

エンジニアの内田 [@spesnova](https://twitter.com/spesnova) です。

2015年8月5日に、[@deeeet](https://twitter.com/deeeet) さんと一緒に Wantedly のオフィスにて Hashicorp Product Meetup と称して、
Hashicorp プロダクトに関する知見、悩み、展望 etc をフランクに共有する会を開きました。

参加者全員がゆるくざっくばらんに話せる場を作りたいと思って招待制のイベントにしました。
参加者の方は [@deeeet](https://twitter.com/deeeet) さんと自分の知り合いの方から、Hashicorpプロダクトを既に利用していたり、導入予定の方々にお声をかけせて頂き、その方々がまた数名招待するという形にしました。
「行きたかった...」というツイートもチラホラありました、、参加できなかった方ごめんなさい。。

どんな内容だったのかをtogetterと以下に簡単にまとめておきます: [http://togetter.com/li/856947](http://togetter.com/li/856947)

![](images/2015-08-06/intro.jpg)

![](images/2015-08-06/audience.jpg)

![](images/2015-08-06/lt_schedule.jpg)

## Working With Terraform by [@glidenote](https://twitter.com/glidenote)
LT のトップバッターは [@glidenote](https://twitter.com/glidenote) さん。

<script async class="speakerdeck-embed" data-id="478b6c4c7d75463388488e8ee465672d" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

Kaizen おなじみの hubot からプルリクを作ってマージしたら CircleCI でデプロイというフローを、 AMI を作るケースでデモされていました。
Packer の実行も、 Packer のバージョンだったり、AWS API を扱えるキー渡したりと案外ちょっと環境依存するので、誰がやっても同じ結果を得るために CI でやるのいいなぁと思いました。Terraform 使おうと思ってる方はスライドに載ってる Terraform 知見は必見です。あと Hashicorp とは関係ないですが、 Kaizen の行動哲学好きです。

ref: [Terraform + GitHub + CircleCI + Atlasを利用してAWSの操作を自動化した - Glide Note - グライドノート](http://blog.glidenote.com/blog/2015/02/18/terraform-github-circleci-atlas-aws/)

## Quipper と Hashicorp by [@hakobera](https://twitter.com/hakobera)

[![](images/2015-08-06/hakobera_slide.png)](https://gist.github.com/hakobera/a5ced7653957a6491047)
[スライド](https://gist.github.com/hakobera/a5ced7653957a6491047)

Quipper でも [@glidenote](https://twitter.com/glidenote) さんのブログで紹介されている CircleCI を使った Terraform 利用を紹介されていた。特徴的なのは Codenize Tool との併用をしていて適材適所で使い分けているところ。また `.tf` ファイルをどのように分けてます？という投げかけがあって、座談会の方では、AWS リソースごとにわける、つまり `ec2.tf` とか `rds.tf` のようにするよりも、プロジェクトごとに分ける方が依存関係とか見やすいよねという話になった。

## 運用自動化に関する話 by [@zembutsu](https://twitter.com/zembutsu)
こちらは非公開になります

## Terraform at Wantedly by [@dtan4](https://twitter.com/dtan4)

<script async class="speakerdeck-embed" data-id="1246047604f0473dbbdd8f47b0912706" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

Wantedly での Terraform 利用例の話。Terraform は Codenize Tools のように既存のリソースの export 機能がないので、新規に追加するリソースにしか導入しづらいのだけど、[@dtan4](https://twitter.com/dtan4) 作の terraforming という便利ツールを使って、既存リソースへ導入していったという話。

ref: [dtan4/terraforming](https://github.com/dtan4/terraforming)

## consul-atlas-alerts by [@rrreeeyyy](https://twitter.com/rrreeeyyy)

<script async class="speakerdeck-embed" data-id="cc1fbf3754674edd9b2079ec29ba0dca" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

Atlas 及び Atlas の Consul 連携について。まず Atlas を実際に使ってる人は自分の観測範囲であまりいないのでとても貴重な話が聞けた。Atlas は CircleCI と被っている部分もあって即採用すべきものでもない。ただ、Consul クラスタを作る際に Atlas に join させるだけで良かったり、 consul-alert 相当のものが Atlas + Consul に搭載されていたりと Atlas 固有のおいしいポイントもあるとのこと。あと [@rrreeeyyy](https://twitter.com/rrreeeyyy) は「れい」と読むことを知った。

ref: [consul & consul-alerts を使った監視システム (hbstyle-2015-01-08)](http://www.slideshare.net/rrreeeyyy117/consul-andalertsmonitoring)

## Go packages from Hashicorp by [@deeeet](https://twitter.com/deeeet)

![](images/2015-08-06/deeeet_slide.png)
[スライド](http://go-talks.appspot.com/github.com/tcnksm/talks/2015/08/hashicorp-meetup.slide#1)

[@deeeet](https://twitter.com/deeeet) さんの話は Hashicorp プロダクトの利用例というよりその内側の話。Hashicorp がプロダクトを作る中で生まれてきた副産物というかライブラリについて紹介されていた。
Golang 使う人には有用な内容だったし、合わせて Hashicorp が利用者のことやバグ報告ちゃんとしてもらうためにわかりやすいエラーを出すといった Hashicorp tao にも言及していて勉強になった。

## Terraform Tips by [@tkak](https://twitter.com/tkak)

<script async class="speakerdeck-embed" data-id="91c928c7b1df430191f8e5955b41b6d7" data-ratio="1.37081659973226" src="//speakerdeck.com/assets/embed.js"></script>

[@tkak](https://twitter.com/tkak) さんの発表。社内独自環境向けに Custom Provider を作る方法だったり、Module について紹介されていた。Chef や Puppet でインフラをコード化したから誰でもインフラのコード触れるよね、と思ったら結局 Chef 職人しか触れないみたいなことと同じく、 Terraform 使って誰でも AWS リソース追加できるねと思ったら今度は RDS のパラメータ良くわかりませんみたいなことは現実に起きてくる。なので、 Module を使ってリソースを抽象化して必要なパラメータを絞ってあげると良いことをこの発表で学べた。

ref: [TerraformのProviderを作った - tkak's tech blog](http://tkak.hatenablog.com/entry/2014/11/07/074044)

## Usecase examples of Pakcer by [@hsbt](https://twitter.com/hsbt)

<iframe src="//www.slideshare.net/slideshow/embed_code/key/fTgmJGwbnqWelu" width="425" height="355" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/hsbt/20150805-hashicorptalks" title="Usecase examples of Packer " target="_blank">Usecase examples of Packer </a> </strong> from <strong><a href="//www.slideshare.net/hsbt" target="_blank">Hiroshi SHIBATA</a></strong> </div>

[@hsbt](https://twitter.com/hsbt) さんによる GMO ペパボでも Packer での AMI イメージ作成事例の話。Packer の中で cloud-init 使ったり、serverspec 流したり、何をイメージ化するか等々 Packer の知見が詰まった発表でした。さらに詳細な話は YAPC でされるとのこと。

## Stretcher in 5min by [@fujiwara](https://twitter.com/fujiwara)

<script async class="speakerdeck-embed" data-id="8d83ac3687ae40c9a68cf7406c1b50e6" data-ratio="1.77777777777778" src="//speakerdeck.com/assets/embed.js"></script>

[@fujiwara](https://twitter.com/fujiwara) さんによる自作のデプロイツール stretcher の話。[@sora_h](https://twitter.com/sora_h) さんの [mamiya](https://github.com/sorah/mamiya) にインスパイアされたとのことで、 S3 に置いたアプリコードを rsync で取得してくる指示を SSH ではなくて consul event でトリガーすることで、スケーラブルかつ速い。10 秒でデプロイが完了するらしい、速い...。こちらも自作の [Consul を使ったダッシュボード](https://github.com/fujiwara/consul-kv-dashboard)と組み合わせたデプロイデモも見せてもらった。

ref: [fujiwara/stretcher](https://github.com/fujiwara/stretcher)

## 座談会
LT のあとは 1 時間くらい皆で自由に話してました。この時間が勉強会の中で一番濃い時間かなと思います。（メモがなくてごめんなさい）

## 最後に
参加してくださった皆さん、イベント開くにあたって協力してくれた同僚の皆さんありがとうございました！
