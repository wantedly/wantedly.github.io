---
title: Chef で Elasticsearch クラスタを EC2 上に作る
date: 2014-03-25 13:25 JST
tags: elasticsearch chef ec2 nginx
wantedly_id: 323185
facebook_id: seigo.uchida
twitter_id: spesnova
github_id: spesnova
---

![](images/es-with-chef.jpg)

エンジニアの内田（@spesnova）です。

[「実践！Elasticsearch」](http://engineer.wantedly.com/2014/02/25/elasticsearch-at-wantedly-1.html) の第二回として、今回は Chef Server を使って Elasticsearch クラスタを AWS の EC2 上に構築する方法を紹介します。

Chef の基本的な部分については説明を省きます。

目次

0. なぜ Chef Solo でなく Chef Server を使うのか
0. 単体の Elasticsearch サーバーを立てる
0. Elasticsearch プラグイン込みで構築する
0. Elasticsearch クラスタを立てる
0. Nginx と Security Group でアクセスを制限する

## なぜ Chef Solo でなく Chef Server を使うのか
Elasticsearch は一旦置いておいて、Chef Server に関する話をします。

Chef Solo を使っている方が多いと思いますが、Wantedly ではインフラの管理に Chef Solo でなく Chef Server を使っています。
なぜかというと Chef の **[search](http://docs.opscode.com/essentials_search.html)** を使いたいからです。

Chef Server は Chef Solo と比べて

* Chef Server の運用が難しい
* 導入コストが高い

というデメリットはありますが、search は非常に魅力的です。

（[グリーのインフラに Chef を導入した話](http://labs.gree.jp/blog/2013/12/10056/) にもあるように、ある程度の規模の会社には内製のサーバー情報管理システムが存在し、Chef Server とバッティングする部分が大きく、より導入に向かいない場合もあると思います。私が以前所属していた会社でも同じような課題がありました。）

一番単純な例だと `nginx::default` recipe が run_list に入っている Chef の node を検索したい場合は、以下のようにします。（`-i` マッチしたオブジェクトの ID だけを返すオプション）


```console
$ knife search node "run_list:recipe\[nginx\:\:default\]" -i

node-1
node-2
node-3
```

search で検索可能なオブジェクトとして

* client
* data bag
* environment
* node
* role

があり、knife コマンドだけでなく、recipe 内、Chef Server Web API からでも search が利用できます。search の詳細については[公式ドキュメント](http://docs.opscode.com/essentials_search.html) に譲るとして、より具体的に何が良いのかを紹介したいと思います。

例えば、ロードバランシングにおいて、バランシング先のサーバーを動的に登録・登録解除することが出来るようになります。
今 haproxy で web サーバーのロードバランシングをしているとします。`/etc/haproxy/haproxy.cfg` を Chef の template resource と search を使って動的に設定します。

`haproxy.cfg.erb`

```erb
...
...
    balance roundrobin

  <% @servers.each do |s| %>
    server <%= s.name %> <%= s.ec2.public_ipv4 %>:80 check
  <% end %>
...
...
```

このテンプレートに渡す web サーバー郡を search を使って取得します。

`your-haproxy-recipe.rb`

```ruby
# recipe 内で search を利用
servers = search(:node, "run_list:role\[web\]")

template "/etc/haproxy/haproxy.cfg" do
  source "haproxy.cfg.erb"
  variables({
    :servers => servers
  })
end
```

こうしておくと、web サーバーが増減した（もちろん web サーバーも Chef Server で構築します）際に haproxy サーバー側で `chef-client` を実行することで、そのときどき web という Chef の role を持った web サーバー郡がロードバランシング先に登録されます。

他の例では、API サーバー群が Auto Scale して数が変動している環境で、API サーバー郡へデプロイしたいとします。
その際今デプロイ対象のサーバーを洗い出すのではなく、Capistrano なり Fabric に Chef Server API 経由で今の API サーバー情報を渡すことで、対象サーバーを気にせずデプロイすることが可能になります。（[Chef ServerとCapistrano3を組み合わせて自動でデプロイ対象サーバを決める方法](http://www.ryuzee.com/contents/blog/6868)とか正にこの話ですね）

監視ツール Sensu が Chef や Puppet 利用を推奨していて、監視対象を自動登録・解除できるのも search を利用しているからですね。

つまり、プロビジョニングだけでなくその後の他のサーバーと繋ぎ込む部分まで Chef に任せられるようになります。

![](https://wiki.opscode.com/download/attachments/24019610/chefsi.png?version=1)

search を使ってインフラをダイナミックにすることでより変化に強いインフラになるのかなと思います。

## 単体の Elastcsearch サーバーを立てる

