---
title: Twilioを使ってみた
date: 2013-12-30
wantedly_id:
facebook_id:
twitter_id: sasa_sfc
---
##はじめに
こんにちは！現在Wantedlyでインターンをさせてもらっている現役高校生の[kento](https://www.wantedly.com/users/2217896)です。
今回はWantedlyの社内ハッカソンに参加させていただいたときに使ったTwilioというAPIについて自分のまとめも兼ねて記事を書かせていただきたいと思います。


##twilioとは
twilioは電話や音声メッセージ、SMSなどを使うことの出来るAPIです。日本語のドキュメントも用意されていて簡単に使えて便利なのですが無料版では使い勝手が凄く悪いので個人で利用する場合は有料アカウントをとらざる終えないので個人ではちょっと敷居の高いアプリとなっています。


##調べたドキュメント
[公式](http://twilio.kddi-web.com/)
[公式チュートリアル](https://jp.twilio.com/docs/quickstart)
[git ruby](https://github.com/twilio/twilio-ruby)

[電話基本](http://blog.twilio.kddi-web.com/2013/05/21/ruby%E3%81%8B%E3%82%89%E9%9B%BB%E8%A9%B1%E3%82%92%E3%81%8B%E3%81%91%E3%82%8B/)
[便利ツール](http://dev.classmethod.jp/etc/twim11/)

##電話機能の使い方
まずは公式ページでアカウント登録をしてtwilow電話番号を取得する

sid, token、twilioの電話番号を取得する(取得するのは米の電話番号が良いですよ!)

その後、Gemのインストールをします

```bash:gem
gem "twilio-ruby"
```

```bash:ターミナル
bundle
```

modelの中に作成したcall.rbに記述するだけ

```ruby:model
class Call
  def self.voice_message
    account_sid = ENV['TWILIO_SID']#中身は自分のものに変える
    auth_token = ENV['TWILIO_TOKEN']#中身は自分のものに変える
    client = Twilio::REST::Client.new(account_sid, auth_token)
    client.account.calls.create(
      from: '+8100000000', # twilio電話番号
      to:   '+8100000000', # 宛先の電話番号
      url: 'http://huntr-static.s3.amazonaws.com/mother/call.xml', #再生される音声の内容が書かれたxmlのURL
      method: 'GET',　#defaltではこれがpostになっているためCall内容が反映されずエラーになるから気をつける
    )
  end
end
```


あとはコンソールで

```bash:コンソール
Call.voice_message
```
とするだけでxmlがパースされたコンテンツの電話がかかってくる

ちなみURLの内容は

```xml:xml
<?xml version="1.0" encoding="UTF-8"?>
<Response>
    <Say language="ja-jp">おかんから、メッセージがあります</Say>//読み上げられる内容
    <Play>http://huntr-static.s3.amazonaws.com/mother/test.mp3</Play>//再生されるmp3
</Response>
```

のような感じで実装できる

今回私は[サーバーダッグ](http://cyberduck.softonic.jp/mac)を使ってファイルをアップしたが勿論なんでもいい
*ただしサイバーダックを使う場合はすべてのファイルをeveryone readのアクセス設定にしてないとエラーとなるので気をつけてください

##SMS機能の使い方
gemをインストールするまでは同じ
あとはコントローラーの中身を変えるだけ

```ruby:コントローラー
class SmsSender
  def self.send_sms
    account_sid = ENV['TWILIO_SID']
    auth_token = ENV['TWILIO_TOKEN']
    client = Twilio::REST::Client.new(account_sid, auth_token)
    client2 = Twilio::REST::Client.new(account_sid, auth_token)

    client.account.messages.create(
      from: '+0000000',
      to:   '+00000000',
      body: "ヽ(･∀･)人(･∀･)ﾉ文章の中身ヽ(･∀･)人(･∀･)ﾉ",
    )
```


*注意　取得したtwilioの電話番号が日本のものである場合はSMSは使えないので注意しましょう。アメリカの電話番号でないとこの機能は使えません。私はこのことに気づかず長い時間を無駄にしました( *´Д⊂ ｸﾞｽﾝ…

##最後に
今回のハッカソンで私は「お母さんアプリ」の名の下に最初に指定した人に録音した励ましの電話をかけるという使い方をしたが
企業の電話対応を自動化したり、
会員登録の際にSMSを使うことでアカウントの複数取得をなくしたり、
そんな真面目な使い方もできるAPIです。楽しかったので機会があればまた使ってみたいです。
