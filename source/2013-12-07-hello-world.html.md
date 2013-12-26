---
title: Wantedly開発チームブログの書き方
date: 2013-12-07
wantedly_id: 10599
facebook_id: yoshinori.kawasaki
---

(※この記事はWantedlyのエンジニアメンバー向けのサンプル記事です)

こんにちは！

このブログは[Middleman](http://middlemanapp.com/)を使って生成され、GitHub Pages上にホストされています。

## 記事を書くには

手元の環境で動かすには以下のようにします。

```bash
$ git clone git@github.com:wantedly/wantedly.github.io.git
$ cd wantedly.github.io
$ git checkout develop
$ bundle exec middleman server
$ open http://localhost:4567/
```

新しい記事を書くには、以下のように過去の記事ファイルをコピーするのが簡単です。

```bash
$ cp source/2013-12-07-hello-world.html.md source/YYYY-MM-DD-TITLE.html.md
```

原稿はMarkdown形式で書きます。Wantedlyで使われている各種プログラミング言語のsyntax highlightも出来ます。

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
$ bundle exec middleman build
$ bundle exec middleman deploy
```

簡単！
