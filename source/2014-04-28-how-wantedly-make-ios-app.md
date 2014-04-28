---
title: WantedlyではどうやってiOSアプリ開発しているのか
date: 2014-04-28
wantedly_id: 10599
facebook_id: yoshinori.kawasaki
twitter_id: kawasy
github_id: luvtechno
---

![Yuri](https://huntr-static.s3.amazonaws.com/engineer_blog/2014-04-28-cover.jpeg)


こんにちは！エンジニアの[川崎](https://www.wantedly.com/users/10599)です。

先週行われた
[Consumer Service Engineer MeetUp Vol.1　~iOS編~](http://eventdots.jp/event/47442)
というイベントで「WantedlyではどうやってiOSアプリ開発しているのか」というテーマで発表してきました。

僕自身の普段の担当は、全体の設計やサーバ側の開発、プロジェクト進行あたりなので、
今回はWantedlyでiOSアプリを「プロトタイピング」し「開発」そして「テスト」するまでで使ってるツール・取り組みをざっくり紹介させていただきました。

意外とこの手の話をする機会はいままでなかったので、
現在開発中のアプリも含め、今現在うちでは何をどうやっているのかまとめられてよかったかなと思います。

以下、発表で紹介したURLなどです。

1. プロトタイピング
    - ホワイトボードでアイデアだし
    - [moqups](https://moqups.com/)でモックアップ作成
    - [Pop](https://popapp.in/)を使って実機でプロトタイプを触ってみる
2. 開発
    - Wantedlyでよく使ってるCocoaPods一覧
        - RestKit - consuming and modeling RESTful web resources
        - AFNetworking - networking framework
        - SDWebImage - Asynchronous image downloader with cache support with an UIImageView category
        - RNCryptor - Encryptor/Decryptor
        - UICKeyChainStore - a simple wrapper for Keychain
        - SVProgressHUD - A clean and lightweight progress HUD
        - TTTAttributedLabel - A drop-in replacement for UILabel that supports attributes, data detectors, links, and more.
        - NUI - Style iOS apps with a stylesheet, similar to CSS
        - JLRoutes - Advanced URL parsing designed to handle complex URL schemes with a block-based callback API
    - [COCOAPODS SEARCH](https://cocoapods.wantedly.com/)でpodの人気度をチェック
    - 使ってる[Objective-Cのスタイルガイド](https://github.com/wantedly/objective-c-style-guide)
3. テスト
    - Rails側のCIは[wercker](http://wercker.com/)で
    - アプリのユーザテスト用に[TestFlight](https://www.testflightapp.com/)で開発版を配信


<script async class="speakerdeck-embed" data-id="0ad89a10b0f50131486d72af66ead636" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>
 



ちなみに、今回のイベントの発表者は自社サービスを開発・運営している会社に限定ということで、
Wantedlyの他にはヴァズ株式会社 (SnapDish)、エニグモ (BUYMA)、はてな、nanapi (アンサー)、
マインドパレット (Snapeee)さんが発表していました。
そのうち主催のほうで他の方の発表のまとめも公開されると思います！
