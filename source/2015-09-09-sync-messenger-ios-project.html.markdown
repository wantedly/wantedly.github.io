---
title: メッセージングアプリSync開発の舞台裏(iOS)
date: 2015-09-09 12:00 JST
tags: iOS, Swift, Rails, AngularJS, Electron, Android
wantedly_id: 631708
twitter_id: susieyy
github_id: susieyy
---


ビジネスシーンで使えるメッセージングサービス[Sync](https://www.wantedly.com/sync)をローンチしました。
その開発の舞台裏をiOSを中心に紹介します。開発のスケジュール、リソース、アプリの規模や進め方など参考になれば幸いです。

サービスについて
----------------------------------

[Sync](https://www.wantedly.com/sync)は社内・社外を問わずプロジェクトやビジネスコミュニケーションがより良い体験なることをゴールに開発しました。以下のURLよりご利用頂けます。
[Web版](https://m.wantedly.com/) , [Desktop版(OnlyOSX)](https://wtd-sync-update-channel.herokuapp.com/download/latest?platform=darwin&channel=production) , [iPhone](https://itunes.apple.com/jp/app/sync-group-messaging-app-for/id1014462508) , [Andorid](https://play.google.com/store/apps/details?id=com.wantedly.android.sync)



![Sync___成果を生み出すグループメッセージアプリ.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/dff18989-a4d7-c754-43d3-4690566ac111.jpeg "Sync___成果を生み出すグループメッセージアプリ.jpg")



アーキテクチャ
----------------------------------


![201500825_Sync_iOSの開発舞台裏_key.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/c835ae0e-092e-4875-0288-ecf80e54857a.jpeg "201500825_Sync_iOSの開発舞台裏_key.jpg")


### サーバ


既存の[Wantedly](https://www.wantedly.com)サーバに並列して、[Sync](https://m.wantedly.com)のサービスをマイクロサービスアーキテクチャ風に構築しています。要素技術や構成はサービスの初期フェイズにおけるスピディーな開発とスモールな運用に適しているものを選定しています。

AccountServerが認証やユーザ情報管理を、APIServerが主要なデータのやり取りをREST形式で提供してます。共にRailsで構築しており[Cookpad](http://cookpad.com/)がOSSで提供している、RESTfulWebAPIを素早くパワフルに開発するためのライブラリ[Garage](https://github.com/cookpad/garage)を採用しています。サーバはAPIのみ提供しておりHTMLをレンダリングするサーバはありません。

メッセージの送受信に必要なリアルタイム通信部分は[Firebase](https://www.firebase.com/)というGoogle傘下のPaaSを利用しています。リアルタイム通信をどのような要素技術を活用するか[WebSocket](https://ja.wikipedia.org/wiki/WebSocket)や[Server Sent Events(SSE)](https://en.wikipedia.org/wiki/Server-sent_events)、[LongPolling](https://en.wikipedia.org/wiki/Comet_(programming))などを検討した結果、[Firebase](https://www.firebase.com/)を選択しました。プッシュ系・プル系のリアルタイム配信では最新の更新情報を受領しても差分更新なのでクライアント側のデータ管理が大変になりがちです。[Firebase](https://www.firebase.com/)は内部では[WebSocket](https://ja.wikipedia.org/wiki/WebSocket)で通信していますが、そこがうまく隠蔽されサーバとクライアントのデータをリアルタイムで同期してくれるので管理の煩わすさから開放されます。また[Node.js](https://nodejs.org/en/)/[Socket.IO](http://socket.io/)などで構築したサーバ群はスケールや運用を行うのはとても骨が折れますがPaaSなので運用面の負担も軽減できます。

- Account Server / [Rails](https://github.com/rails/rails) & [Garage](https://github.com/cookpad/garage)
- API Server / [Rails](https://github.com/rails/rails) & [Garage](https://github.com/cookpad/garage)
- Image Server / [Sinatra](https://github.com/sinatra/sinatra/) & [ImageMagick](http://www.imagemagick.org/script/index.php)
- Realtime Server / [Firebase](https://www.firebase.com/)


### クライアント

クライアントはマルチプラットフォームに対応してサービスを提供しています。Web&Desktopはシングルページアプリケーション（ [AngularJS](https://angularjs.org/) & [Electron](http://electron.atom.io/) )で構築しています。Desktop版はWindows版が開発中でOSXのみ利用頂けます。iOSはSwiftの関数的な機能を活用して開発しています。 AndroidはJavaで開発しています。

- Web&Desktop / [AngularJS](https://angularjs.org/) v1.4, [Electron](http://electron.atom.io/)
- iOS / Xcode6.4, Swift v1.2 iOS8〜
- Android / Android Studio v1.3.2, Android v4.0.3〜5.1.1


チーム
----------------------------------

チーム編成は最大時で以下のような体制で常時フルコミットで参画してるのはそのうちの５名ほどです。iOSの体制が厚いので新規機能を率先して開発していました。

![201500825_Sync_iOSの開発舞台裏_key.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/09962764-0e16-672e-ff15-08927d239d65.jpeg "201500825_Sync_iOSの開発舞台裏_key.jpg")


Product Owner & API Server
CTO @kawasy

Web & Desktop
Engineer @imaimiami / @creasty


iOS
Engineer @susieyy / @morizotter / [@smztko](https://github.com/smztko) / Desiner @ferasyasin@github

Android
Engineer @cattaka / Desiner [@yanAoym](https://github.com/yanAoym)

fastlane
Engineer @hedjirog




スケジュール（iOS）
----------------------------------

![201500825_Sync_iOSの開発舞台裏_key.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/84c7910f-0efe-cb67-7246-888cb28e0c2b.jpeg "201500825_Sync_iOSの開発舞台裏_key.jpg")


サービスの開発は５月からスタートしiOSは３ヶ月間で申請まで行いました。iOSの開発リソースは６人月ぐらいです。最初の１ヶ月はプロトタイプ開発期間としてコードレビューもなく１人ででゴリゴリとコードを書きつつ、基本的な通信部分やMVVMアーキテクチャの実装、共通ロジックの用意などを行いました。本開発の始まった６月からは２名のエンジニアが追加となりプルリクエストのコードはレビューを行う体制で進めました。

進め方
----------------------------------

上記のスケジュール図のようなざっくりな工程表と、要件一覧をもとにプロジェクトがスタートしました。２週間を１イテレーションとしてマイルストーンにタスクを入れてゆるいアジャイル風な運営で進めています。タスクをイテレーションの最初にある程度担当者にアサインはしつつも、進み具合でアサインを変更したり、マイルストーン間のタスクのを入れ替えたりと臨機応変さとスピード感を重視しています。実装を進めていく中で当初計画の要件に対してフィードバックを元に大きく機能を追加したり、実装済みでも大きく機能を削ったりと、より良い体験を作り上げることをゴールにドラスティックな変更を行いつつ開発しました。

ミーティングを必要最低限に抑えることでコーディングの時間をより多く確保しました。実装が始まる前の要件定義の段階で集中的にミーティングを重ねプロトタイプやデモを作って認識を合わせつつサービスの具体的なイメージをしっかり共有しました。実装の具体的な個々の仕様については、GitHubイシュー上で非同期で行い議論の証跡と結論や次のアクションを明文化しました。


ドッグフーディングとユーザフィードバック
----------------------------------

![dogfooding.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/74aa07b7-9593-97f1-c144-d9afe60ee533.jpeg "dogfooding.jpg")


ドッグフーディング（Dogfooding）とは、自社サービスを開発者自らが日常的に利用して問題点を早期に発見したりユーザー視点で品質やＵＸを確認することです。


開発開始から２週間でチームで利用していた[Slack](https://slack.com/)から乗り換えることを目標にしました。自分たちから積極的に利用することで開発者である自分たちからまずファンになることを大事にしました。１ヶ月ごろから社内の他のチームも[Slack](https://slack.com/)から乗り換えてもらい、たくさんのフィードバックを受けて安定性の向上と改善に勤めました。社内で実績を築いたことで２ヶ月ごろから身近な社外の方々にも声をかけて使ってもらい、さらに多くのフィードバックを頂きました。


メトリクス（iOS）
----------------------------------

2015/09/05 時点です。開始からだいたい４ヶ月（８０営業日ぐらい）ほど経過しています。


#### Github上の主要なメトリクス

プルリクエストはできるだけ小さい単位で送り合ってコンフリクト軽減とコードレビューしやすいように工夫をしています。プルリクエストがほとんどないプロトタイプ期間を省くと１日平均１８件ぐらいになります。仕様やタスク、バグレポートなど明文化するものはすべてGitHubのイシューにして情報をすべてリポジトリ内で一元的に管理しています。すべてのプロジェクト情報がGitHub内ある、GitHub探せば見つかる状態を作っています。

- 4,700 Commits
- 1,050 Pull Requests Closed
- 864 Isusses Closed 83 Open ( Total 947 )

イシューの内訳です。Bugのイシューが一番多いです。Feedbackはローンチ前にTestFlightとFabricBetaで社内外に配布して使ってもらったフィードバックの数です。

- Improve 289 (30%)
- Bug 492 (51%)
- Feedback 64 (7%)
- Other(メモ、仕様、アイデアetc) 102 (12%)


#### コードステップ数（iOS）

Swiftのコードが１４１ファイル、１万９千行ほどですがフルコンパイルにPodsライブラリも合わせて４分!!ほどかかります。

```shell
$ cloc
     288 text files.
     285 unique files.
      74 files ignored.

http://cloc.sourceforge.net v 1.64  T=1.36 s (157.4 files/s, 18819.8 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Swift                          141           3157           1698          18708
JSON                            66              0              0           1488
Objective C                      3             90            116            212
C/C++ Header                     4             28             27             63
-------------------------------------------------------------------------------
SUM:                           214           3275           1841          20471
-------------------------------------------------------------------------------
```

#### 画面数

ViewControllerは平均３００行（空行なし）なので、ViewControllerだけで１万２千行になり全体の６４％になります。ストリーボードのファイルはコンフリクトしやすく１つのファイルにたくさんの画面を作成すると非常に遅くなるので細かく分割しています。

- 約２５画面
- ４２ ViewControllers
- ２３ Storyboards

#### ライブラリ数

Swiftの機能を活かしたライブラリを積極的に取り入れています。Swiftライブラリを[CocoaPods](https://cocoapods.org/)でインストールすると、コンパイル時間が長くなるので事前にフレームワークを作成できる[Carthage](https://github.com/Carthage/Carthage)も利用しています。

- [Carthage](https://github.com/Carthage/Carthage) 7 Swiftライブラリ
- [CocoaPods](https://cocoapods.org/) 3 Swiftライブラリ / 33 ObjCライブラリ
- Total 43 ライブラリ


Swiftコンパイル時間
----------------------------------

![201500825_Sync_iOSの開発舞台裏_key.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/ea8b7162-d30e-fb17-25c8-25e920afe31a.jpeg "201500825_Sync_iOSの開発舞台裏_key.jpg")

MacBookPro (15-inch, Late 2013)でフルコンパイル時間が４分以上もかかっていたので以下の施策を行いました。

#### MacBookProを２台体制で開発する

レビューなどでブランチを切り替えると、Podsのインストールや、フルコンパイルが必要だったりするので２台体制で行いました。コンパイル時間も長かったので、待ち時間の有効活用に繋がり効率的に開発を進めることができました。

#### コンパイル時間を短縮する

４分以上コンパイルに必要になったころから、コンパイル時間の短縮化を行いました。４分１０秒からー８０秒の２分５０秒になりました。 

- 型推論しないで型を明記する （ArrayやDictionaryも）
- 複数のswiftファイルを一つにまとめる
- 継承しないclassはfinalを明記する
- Cartage対応のライブラリはPodsでインストールしない


fastlane（iOS）
----------------------------------

![201500825_Sync_iOSの開発舞台裏_key.jpg](https://qiita-image-store.s3.amazonaws.com/0/4943/ffcbacf4-6bc7-72ae-decb-827ace76f764.jpeg "201500825_Sync_iOSの開発舞台裏_key.jpg")

[fastlane](https://fastlane.tools/)を活用してビルド、テスト、配布までの工程を自動化しました。プルリクエストがレビューされマスターにマージされる度に自動で配布されます。常に最新のマスターの状態のリリースビルドを手元で常に確認できるようになりました。また配布が容易になることで、社内へのドックフーディング、社外へのユーザフィードバックなどローンチ前にたくさんの方に使ってもらいやすくなりました。

マージマスターの配布はエンジニアとテスターに留め、ある程度安定していることを確認してから２，３日に一度社内外へ配布していました。


まとめ
----------------------------------

このような背景で作られたサービスがどんなのか気になってくれ方是非使ってみてください！

- [Syncについて](https://www.wantedly.com/sync)
- [Web版](https://m.wantedly.com/)
- [Desktop版(OnlyOSX)](https://wtd-sync-update-channel.herokuapp.com/download/latest?platform=darwin&channel=production)
- Windows版は開発中です
- [iPhone](https://itunes.apple.com/jp/app/sync-group-messaging-app-for/id1014462508)
- [Andorid](https://play.google.com/store/apps/details?id=com.wantedly.android.sync)
