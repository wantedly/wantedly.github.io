---
title: Hashicorp Product Meetup やりました
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
参加者の方は [@deeeet](https://twitter.com/deeeet) さんと自分の知り合いの中からでなんとなく 「Hashicorp プロダクトを使ってる、使いたい」雰囲気を感じる方々にお声を掛けさせてもらって、その方々がまた数名招待するという形にしました。「行きたかった...」というツイートもチラホラあって、、ごめんなさいです。。

どんな内容だったのかを簡単にまとめておきます。

## Working With Terraform by [@glidenote](https://twitter.com/glidenote)
LT のトップバッターは [@glidenote](https://twitter.com/glidenote) さん。

<script async class="speakerdeck-embed" data-id="478b6c4c7d75463388488e8ee465672d" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

Kaizen おなじみの hubot からプルリクを作ってマージしたら CircleCI でデプロイというフローを、 AMI を作るケースでデモされていました。
Packer の実行も、 Packer のバージョンだったり、AWS API を扱えるキー渡したりと案外ちょっと環境依存するので、誰がやっても同じ結果を得るために CI でやるのいいなぁと思いました。Terraform 使おうと思ってる方はスライドに載ってる Terraform 知見は必見です。あと Hashicorp とは関係ないですが、 Kaizen の行動哲学好きです。

## Quipper と Hashicorp by [@hakobera](https://twitter.com/hakobera)

[![](images/2015-08-06/hakobera_slide.png)](https://gist.github.com/hakobera/a5ced7653957a6491047)
[スライド](https://gist.github.com/hakobera/a5ced7653957a6491047)

## Go packages from Hashicorp by [@deeeet](https://twitter.com/deeeet)

