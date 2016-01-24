---
title: Wantedly エンジニアチームは湯河原温泉で開発合宿をしてきました！
date: 2016-01-24 22:08 JST
tags: Rails, PostgreSQL, Development, Camp
wantedly_id: 3454376
github_id: south37
cover_image: https://qiita-image-store.s3.amazonaws.com/0/10920/5d37023f-a7c2-f57a-cf97-320d2f2b349b.jpeg
---
![Wantedly開発合宿](https://qiita-image-store.s3.amazonaws.com/0/10920/5d37023f-a7c2-f57a-cf97-320d2f2b349b.jpeg)

こんにちは、Wantedly のエンジニアの南直 [@south37](https://github.com/south37) です！

先日、Wantedly では湯河原での開発合宿を行いました！その際、「目標をあらかじめ決める」、「1日目はお酒を飲まずに開発に集中する」という2つの約束事を実践したところ、想像以上に開発に集中でき、きちんと成果も出す事ができました！

自分たちにとっても想像以上に良い結果となったので、その経緯をまとめたいと思います！！

## 開発合宿の経緯
今回の開発合宿は、「きちんと時間を取らないと取り組めない事」をやりたいというモチベーションから始まりました。取り組む候補としてはマイクロサービス化を進める事や Rails のバージョンを上げる事、RabbitMQ の様な新しいミドルウェアを試してみる事など色々ありましたが、最終的には全てひっくるめて「Wantedly のサイトを 20%スピードアップする」という大きな目標を立てました。

成果を出せば第二回開発合宿にも繋がるんじゃないかという期待から、僕らのモチベーションも上がりました。

## 合宿の様子
それでは、実際に合宿の様子について書きたいと思います。今回お邪魔したのは 「おんやど恵」という湯河原の温泉旅館で、12/21~12/23 までの2泊3日の合宿でした。「おんやど恵」は開発合宿用の設備を整えていて、 [増井さんが行っていたり](http://engineer.typemag.jp/article/furograming)、[ハウテレビジョンさんが行っていたり](https://codeiq.jp/magazine/2015/11/32232/)して、開発合宿先として人気の旅館の様です。評判と設備を見て、僕らもここに決めました。

## オフィスからの出発
12/21(月) の 14:00 から始まるエンジニア全体ミーティングを終えた後、合宿組はおもむろに出発しました。

合宿に向けて、心なしか浮き足立つ面々。思わず笑みがこぼれています。

![_DSC0007.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/f0d01901-ddfd-05f6-1aa4-d38684fccdcb.jpeg "_DSC0007.JPG")

![_DSC0008.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/492266f7-e8ff-f509-8673-99c252d1e461.jpeg "_DSC0008.JPG")

![_DSC0010.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/9ea20f77-18e8-75e9-ca44-d54700f7a7bb.jpeg "_DSC0010.JPG")

湯河原までは、電車で向かいます。

![_DSC0025.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/bd04c523-9beb-8c0a-e8b4-080c9f8daad7.jpeg "_DSC0025.JPG")

![_DSC0032.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/b2be2441-b69a-094e-64ca-bc0b768975d9.jpeg "_DSC0032.JPG")

![_DSC0036.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/0eda9646-d34d-c68e-f54b-6965ed359bde.jpeg "_DSC0036.JPG")


湯河原到着！！さらに、巡回バスで一本で「おんやど恵」に到着！！バスですぐにこれるのは便利ですね！！

![_DSC0046.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/e5e35457-fca6-4428-e302-8462c34c3f2a.jpeg "_DSC0046.JPG")

![_DSC0050.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/c3fa892b-53b6-93be-0f26-5557cbcfd5c5.jpeg "_DSC0050.JPG")

## 1日目の開発開始 (17:30)

着いたのは 17:30 頃、夕食は 18:30 からと聞いて、この1時間を無駄にしない為に早速開発を始めました。

「おんやど恵」さんは開発合宿に力を入れているだけあって、開発環境がかなり充実していました。48時間いつでも好きに使って良い会議室が一部屋（10人が余裕を持って座れる広さ）いただけて、大量の電源タップとホワイトボードが設置されていました。更に、無線LAN は高速かつかなり安定していて、ネットワーク関係でトラブルになる事は全くありませんでした。実測値で常時下り 30MBps 出ていたので、開発するには充分だと思います。


![_DSC0055.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/5cc288f9-0e71-1aa9-5a21-4e2359541935.jpeg "_DSC0055.JPG")

![_DSC0056.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/bc2c191d-97bc-b8aa-015b-fca88009c315.jpeg "_DSC0056.JPG")

![_DSC0064.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/53a21b67-6994-7e6f-c2ee-00dec105b5db.jpeg "_DSC0064.JPG")

最初の1時間は、手を動かすというよりは方針決めの時間にしました。「Wantedly を 20%高速化する」為に何ができるか、そもそも何の値を使って「20%」を出すのかというとこから話して、以下の方針を決めました。

- 最終ゴールは、NewRelic の BROWSER タブで確認出来る「Brower page load time」の平均を 20% 早くする事
- その他、個別のページや RDB のレスポンスタイムなど、より細かい単位での改善&ベンチマークも行う（最終ゴールが達成できなかった時の保険の意味もありましたw）
- 1チーム1~3人くらいで幾つかにチーム（タスク）を分けて、それぞれで個別の最適化を行う。大きく分けて以下のチームが存在した
  - リクエストが集中しているページの高速化（Wantedly はサイトの特性上「募集ページ」や「募集 Widget」へ極端にアクセスが集中していた。個々の resopnse はそこそこ早いもの Brower page load time で見ると全体の 58% を占めていたので、ここの最適化が必須と感じた。）
  - RDB のチューニング（Wantedly は RDS で PostgreSQL を使っていて、これまでチューニングに力を入れてきていなかった。その為、最適化の余地はかなりあると思っていた。[これについては @awakia が Qiita にもまとめている](http://qiita.com/awakia/items/9981f37d5cbcbcd155eb)）
  - JavaScript ファイルのロードタイミングの最適化（HTML のパース中に script タグが現れると、スクリプト実行によってページのレンダリングはブロックされる。その為 script タグはページ末尾に集める事がベストプラクティスとなっているが、そのベストプラクティスが守られていないページが幾つか存在した）
  - リソースの非同期読み込みの徹底（scroll でしか現れない画像など、first view では現れない要素を非同期に）
  - 社内用管理画面の高速化（ユーザーは目にしないが、その為に雑な実装になっている部分が多くあったので、最適化を行った）
- 出来れば1日目で目標を達成して、2日目はゆったり湯河原を楽しむ！！！

方針を決めたところで良い感じに夕ご飯の時間になりました。

## 1日目の夕食 (18:30)
さて、待ちに待った夕食です。おんやどの夕食は「ザ・旅館のご飯」という感じで、様々な美味しいご飯が次々に運ばれてきました。

![_DSC0083.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/4a0e564a-7e8d-0a22-75c0-195c4d1b7aee.jpeg "_DSC0083.JPG")

最初に頂いたのは数の子や昆布などの珍味。

![_DSC0079.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/215df7e4-96d0-b3bf-c75c-9dc845707b6e.jpeg "_DSC0079.JPG")

次に頂いたのはお刺身。美味しかったです。

![_DSC0085.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/5f541171-c5d8-0a4b-a5b8-93c126d875a0.jpeg "_DSC0085.JPG")

お蕎麦。これも美味しかったです。

![_DSC0090.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/d00487ef-2dfa-e0cc-54b1-9074511533f2.jpeg "_DSC0090.JPG")

煮物。僕は大根が大好きです。

![_DSC0100.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/d68afd1e-d2d0-cbe9-c273-0a248423a9c7.jpeg "_DSC0100.JPG")

天ぷら。

![_DSC0102.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/bcae7a3a-d27f-184b-21f7-346ec20f7bd7.jpeg "_DSC0102.JPG")

そしてお鍋に入れて頂くお肉！！たまりませんね！！！

![_DSC0105.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/d79f615d-8faa-7197-3636-011127c62f73.jpeg "_DSC0105.JPG")

![_DSC0112.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/735472b7-3564-b3f9-84aa-a199526e9c74.jpeg "_DSC0112.JPG")

次々運ばれてくる美味しい食事に、思わず笑みがこぼれます。

![_DSC0088.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/70de5daa-9d86-c624-d6f2-c5aaa413424d.jpeg "_DSC0088.JPG")

こうして美味しく夕食をいただいた後は、温泉へ向かいました。（尚、僕らは1日目で何とか高速化を達成しようと意気込んでいた為、お酒は飲みませんでしたw これも2日目に楽しむ為の投資です）

## 温泉
温泉は、室内の温泉に加えて、露天風呂も付いていました。
露天風呂に浸かって、英気を養う面々。とても気持ちが良かったです。

![2015-12-22_21_51_47.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/24e09208-374e-8c6f-57a6-115226be301f.jpeg "2015-12-22_21_51_47.jpg")

足湯&喫煙コーナーも、癒しの場になりました。

![2015-12-22 20.39.23.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/5401e3cd-6c6f-3896-4c55-91a3143401d7.jpeg "2015-12-22 20.39.23.jpg")

## 開発再開 (20:30)
温泉を堪能した後は、いよいよ開発再開です。浴衣に着替えてはいますが、完全にガチモードです。各自、自分のタスクに没頭しました。

![2015-12-21 20.32.42.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/baa0ae93-d8f8-5425-b605-c2056a0f845e.jpeg "2015-12-21 20.32.42.jpg")

![2015-12-22 00.51.17.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/c1acafc7-2f74-9970-b8f9-fbc2a0c370fc.jpeg "2015-12-22 00.51.17.jpg")

![2015-12-21 23.21.06.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/06650f8d-b48e-5aa5-cd7e-fae4cf8542ee.jpeg "2015-12-21 23.21.06.jpg")

開発は次の日の朝 6:00 ごろまで夜通し行われました。

![2015-12-21_23_21_00.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/cc3e5e4f-3ab5-a358-976a-053537cbf73e.jpeg "2015-12-21_23_21_00.jpg")

![2015-12-22_01_12_22.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/c8a70e93-3739-8a53-9ab8-e6cbffdd7b80.jpeg "2015-12-22_01_12_22.jpg")

![2015-12-22_02_51_51.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/0ed56ab3-d969-cdcf-f435-cac250958bef.jpeg "2015-12-22_02_51_51.jpg")

![2015-12-22_05_29_00.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/1864573a-d2af-511d-a27b-dd79209b2d2f.jpeg "2015-12-22_05_29_00.jpg")

## 2日目
前日の作業が明け方まで続いた事から、次の日はなかなか起きれない。。。と思ったのですが、旅館のとてもパワフルな仲居さんに起こされて、ちゃんと朝食を食べる事が出来ました。

![IMG_3019.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/d2ce3012-3a90-4dbd-3b23-a96b99bee318.jpeg "IMG_3019.jpg")

![2015-12-22 08.39.32.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/41ad1105-83e1-3ca1-3835-4d29fbf28286.jpeg "2015-12-22 08.39.32.jpg")

![2015-12-22 08.54.08.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/84194d7f-a9d8-b426-87f0-d1eddcff786a.jpeg "2015-12-22 08.54.08.jpg")

![2015-12-22 08.43.32.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/c40013ec-2c36-cfda-bfb5-1fb6ffc55434.jpeg "2015-12-22 08.43.32.jpg")


朝食の後は、引き続き開発を行います。作業は進んでいたもののまだ 20% の高速化は達成できていなかった為、皆少し焦りながら開発をします。

![2015-12-22 10.38.39.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/a6ca3c78-8dc2-5477-9872-aad1f19d0b5c.jpeg "2015-12-22 10.38.39.jpg")

![2015-12-22 10.38.46.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/90d53051-da10-4d18-1549-2fb8ada7e91d.jpeg "2015-12-22 10.38.46.jpg")

集中して作業していると、気がつけば 14:30 に。さすがにお腹が空いてきたので、お昼ご飯に向かう事にしました。近辺のお店を検索してみて、ワンタンが美味しいと噂の「王ちゃん」というお店に向かうことにしました。

![2015-12-22 14.41.22.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/c2da63a4-bf1f-92f7-df77-4f901dadacb9.jpeg "2015-12-22 14.41.22.jpg")

外を歩くと自然が広がっていて、良い気分転換になります。

![2015-12-22 15.58.08.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/6d2e08a7-33b1-d239-08c2-61a87d93f540.jpeg "2015-12-22 15.58.08.jpg")

![2015-12-22 14.48.13.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/23b771d3-17da-104e-5afa-282ed71dd34e.jpeg "2015-12-22 14.48.13.jpg")

![2015-12-22 16.01.40.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/b9ae16a5-0365-6462-8d21-028905e8d74a.jpeg "2015-12-22 16.01.40.jpg")

お店は老夫婦でやってらしていて、人数が多かったのでカウンターと座敷に分かれてご飯をいただきました。

![IMG_3080.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/db3d9389-81d2-0c05-21b7-15a25c6f7c3d.jpeg "IMG_3080.jpg")

![2015-12-22 15.06.51.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/2c4255d7-0d6d-cc14-c8e4-fd0a58b72cbd.jpeg "2015-12-22 15.06.51.jpg")

料理の写真は取り忘れてしまいましたが、食べログのページにたくさん写真があったので興味が湧いた方は見て見てください！
[王ちゃん - 熱海/ラーメン [食べログ]](http://tabelog.com/shizuoka/A2205/A220502/22024811/dtlrvwlst/)

昼食の後は近くにあった公園でちょっと遊んでから、旅館に戻ってきました。

![IMG_3154.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/83d383d3-18cd-440f-558b-c0fe2cc5adaa.jpeg "IMG_3154.jpg")

![IMG_3268.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/384f25f7-30d6-54b5-ed27-3fe14b60aafb.jpeg "IMG_3268.jpg")

![2015-12-22 16.10.18.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/3b59d603-ae2f-6eec-f2a4-8e40a1c0bfa4.jpeg "2015-12-22 16.10.18.jpg")

旅館に戻るとすぐさま開発に移ります。結果を出す事を求められている為、どこまでもストイックです。

![2015-12-22 17.58.20.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/922d8688-a1f3-55f9-0573-6549414e44e0.jpeg "2015-12-22 17.58.20.jpg")

気がつけば 2日目の夕食の時間が迫ります。ここで成果を確認したところ、 Brower page load time が 28% 改善出来ている事が分かりました。目標達成です！！！

![2015-12-23 00.58.51.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/eddbe1b3-38a5-c38e-afb2-79fedc23f1ad.jpeg "2015-12-23 00.58.51.jpg")

## 2日目夕食 (19:00)
目標が達成できた為、最高に良い気分で夕食を楽しむ事が出来ました。
お酒も解禁です。みんなで、「20%高速化」達成を祝って乾杯をしました。

![_DSC0143.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/5d37023f-a7c2-f57a-cf97-320d2f2b349b.jpeg "_DSC0143.JPG")

2日目の夕食もとても豪華でした。

![2015-12-22 19.19.22.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/be09b441-0892-fd92-4608-4fd17f497b29.jpeg "2015-12-22 19.19.22.jpg")

![_DSC0135.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/88bc6058-22bb-5538-97f9-582172ab878b.jpeg "_DSC0135.JPG")

![_DSC0134.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/c8a0902f-871b-b71e-5e1c-0285567ae6c7.jpeg "_DSC0134.JPG")

![_DSC0136.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/57d7e250-ca49-7058-2abd-c9d1216905b0.jpeg "_DSC0136.JPG")

![_DSC0139.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/d71b8b94-63a4-7a83-231e-d738ecd0a393.jpeg "_DSC0139.JPG")

![_DSC0148.JPG](https://qiita-image-store.s3.amazonaws.com/0/10920/4ffc0f65-bc78-4ce0-a58b-2adfff0075f7.jpeg "_DSC0148.JPG")

夕食後は温泉に浸かり、さらに近くのセブンイレブンで宴会用のお酒やおつまみを買ってから、会議室へ向かいます。会議室なら広くてみんなで集まって話しやすいので、宴会にぴったりだろうという判断でした。

## 開発再開
目標は達成したとはいえやりかけの作業や PR も残っていたので、会議室に着くと自然と開発が再開しました。適当な時間になったら自然と飲み会が始まるだろうと誰もが思っていました。

![2015-12-22 22.50.52.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/c0eaf2d2-d997-99a2-445c-fa4c81c0defb.jpeg "2015-12-22 22.50.52.jpg")

ところが、これが最大の誤算でした。エンジニアの性なのか、やりかけのタスクとPCを目の前にするとどうしてもコードを書き続けてしまい、気がつけばほとんどお酒を飲まないまま 2:00 に。

![2015-12-23 01.20.36.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/a71f49ff-24bb-2334-ec83-b76aa08e7ae8.jpeg "2015-12-23 01.20.36.jpg")

流石に眠くなってきたので、部屋に戻ってゆっくりと眠りに着きました。

![2015-12-23 02.22.51.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/3bd5ef36-b967-c697-59dc-545fe3eb15ec.jpeg "2015-12-23 02.22.51.jpg")

## 3日目
3日目の朝も、美味しい朝食を頂きました。

![2015-12-23 08.41.27.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/e5c8d967-ccae-17d9-91c3-0c03fee54b6c.jpeg "2015-12-23 08.41.27.jpg")

もう目標は達成できているので、朝食後は部屋でゆっくりします。幸せな時間です。

![2015-12-23 09.20.09.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/8c471b8c-47fa-4c69-5bc3-f9c865a933de.jpeg "2015-12-23 09.20.09.jpg")

![2015-12-23 09.20.31.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/451abaa3-b683-b417-8fe6-67014919e140.jpeg "2015-12-23 09.20.31.jpg")

10時がチェックアウト、11時に会議室を出なければならないとの事だったので、荷物をまとめて部屋を後にします。3日間のほとんどを過ごした会議室を離れるのは、なんだか感慨深いものでした。

![2015-12-23 10.57.28.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/5c104ce1-5494-cc4a-f484-f192c67edb10.jpeg "2015-12-23 10.57.28.jpg")

![2015-12-23 11.19.01.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/58e0228e-758f-a9b4-ff8c-01e3810b26ee.jpeg "2015-12-23 11.19.01.jpg")


宿からはバスで駅へ向かうので、バスの時間までは思い思いの過ごし方をします。エントランスでゆっくりしたり、足湯に浸かって癒されたり。足湯はとても気持ち良くて、コーディングにもぴったりです。

![2015-12-23 11.26.28.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/a7df2ab8-9c7c-1dbb-817d-a4b7c7b78c81.jpeg "2015-12-23 11.26.28.jpg")

![2015-12-23 11.22.47.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/1abb8650-ecb5-8aa2-c7df-6d94e4686766.jpeg "2015-12-23 11.22.47.jpg")

存分に満喫してから、3日間お世話になって旅館に別れを告げて、帰ってきました。「おんやど恵」さん、ありがとうございました。

![IMG_3483.jpg](https://qiita-image-store.s3.amazonaws.com/0/10920/b0852b67-b1ff-cc29-906e-b9dbb112e858.jpeg "IMG_3483.jpg")

## 開発合宿を振り返って

まずは成果についてですが、目標であった「Brower page load time の 20% 高速化」を達成する事が出来ました！

### Before(3.81 s)

![before.png](https://qiita-image-store.s3.amazonaws.com/0/10920/644d5e05-b930-342e-2d24-b7ac00a2f80f.png "before.png")

### After(3.02 s)

![after.png](https://qiita-image-store.s3.amazonaws.com/0/10920/f3ae9f1b-b7f3-c09e-80ba-b94789e51a1d.png "after.png")


### Dom Processing
また、 DOM processing に限定すると、 1.85s => 1.1s で 41% の高速化が出来ました！
![dom-rendering.png](https://qiita-image-store.s3.amazonaws.com/0/10920/29750940-4afe-c101-5a67-58328eae1ce4.png "dom-rendering.png")


### PostgreSQL
PostgreSQL のパラメータチューニングの結果も、 31ms -> 23ms で 25％ の高速化が出来ました！
![rds.png](https://qiita-image-store.s3.amazonaws.com/0/10920/9008d3f5-486c-a6da-4a9a-e9ac00e0ad64.png "rds.png")

その他細かい部分での改善も出来て、総じて良い結果となったと思います。

### 良かった点について
事前に目標を明確にしていた事と、開発の初期段階で目標達成の為の作業の方向性を（現状の数字を見ながら）決めれた事が良かったんじゃないかと思っています。また、遊ぶのは目標を達成してからにしよう、と心を鬼にして決断できたのも大きかったと思います。

### 反省点について
2日目の夜は目標を達成できていたので大いにはしゃぐ予定だったのですが、エンジニアの性なのかPCを前にすると気がつけばコードを書いていました。ここは反省点だと思っていて、無理矢理にでもイベントを用意すべきだったと思っています。次に開発合宿をする際は、目標を達成するだけでなくレクリエーションにも力を入れたいと思っています。

## 最後に
今回、Wantedly で開発合宿をやってみるのは初めての挑戦でした。本当にちゃんと集中して開発ができるのか、パフォーマンスが出せるのかなど不安も大きかったのですが、蓋を開けてみれば大成功とも言える結果でした。
今後も定期的に開発合宿を実施していく予定です！Wantedly の開発合宿に興味が湧いた方は、ぜひ気軽に話を聞きに来てください！！




