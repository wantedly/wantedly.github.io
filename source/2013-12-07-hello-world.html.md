---
title: Wantedly開発チームブログの書き方
date: 2013-12-07
wantedly_id: 10599
facebook_id: yoshinori.kawasaki
twitter_id: kawasy
---

(※この記事はWantedlyのエンジニアメンバー向けのサンプル記事です)

こんにちは！

このブログは[Middleman](http://middlemanapp.com/)を使って生成され、GitHub Pages上にホストされています。
MiddlemanはRubyで書かれた静的サイト生成のフレームワークで、gemとして提供されています。

## 記事を書くには

手元の環境で動かすには以下のようにします。

初回はまずレポジトリをcloneしてとってきましょう。
ちなみに、`develop`ブランチに元原稿が存在し、`master`ブランチに公開するHTMLが自動的に生成されます。

```bash
$ git clone git@github.com:wantedly/wantedly.github.io.git
$ cd wantedly.github.io
$ git checkout develop
$ bundle install
$ bundle exec middleman server
$ open http://localhost:4567/
```

2回目以降は、手元の`develop`ブランチを最新にするだけです。

```bash
$ git pull origin develop
$ bundle exec middleman server
$ open http://localhost:4567/
```

新しい記事を書くには、以下のように過去の記事ファイルをコピーするのが簡単です。

```bash
$ cp source/2013-12-07-hello-world.html.md source/YYYY-MM-DD-TITLE.html.md
```

適当にbranchを作ってpull requestを送ってください。

原稿はMarkdown形式で書きます。画像を使ったり、Wantedlyで使われている各種プログラミング言語のsyntax highlightも出来ます。

- Ruby

```ruby
def my_cool_method(message)
  puts message
end
```

- CoffeeScript

```coffeescript
$ ->
  console.log 'hi'
```

- SQL

```sql
SELECT COUNT(*) FROM users
```


## 記事を公開するには

以下のようにすると、HTMLファイルが生成されGitHubの`master`ブランチに`git push`されて、自動的に公開されます。

```bash
$ bundle exec middleman deploy
```

簡単！
