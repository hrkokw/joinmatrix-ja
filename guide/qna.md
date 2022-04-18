---
title: 質問と回答
layout: page-two-col
nav: false
parent: guide
permalink: guide/qna/
---

## 質問と回答 {#questions-and-answers}

はじめに、いくつかの点について明確にしておきます。

## Matrixに関するここ以外のガイド {#other-matrix-guides}

以下のガイドにはホームサーバに特化した設定方法が含まれていますが、多くの内容はMatrixの連合ネットワークにも当てはまるものです。

* [matrix-help.envs.net](https://matrix-help.envs.net/)
* [Matrix at TU Dresden](https://doc.matrix.tu-dresden.de/en/)

## このガイドについて {#about-this-guide}

このガイドは多くの皆様の協力を得ながら、[Austin Huang](https://austinhuang.me)によって執筆されています。皆様のご協力に深く感謝します。

`joinmatrix.org`のドメインは、[Privacy Guides](https://www.privacyguides.org/)を代表して[Jonah Aragon](https://www.jonaharagon.com/)氏より提供されています。この貢献にもまた、深く感謝します。

本サイトのすべてのコンテンツには[Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)を適用します。このWebサイトへのリンクをお願いします。

ロゴマークはこれらの作品からの派生物です。

* [Matrix icon](https://commons.wikimedia.org/wiki/File:Matrix_icon.svg).
* [Green Stylish Arrow](https://commons.wikimedia.org/wiki/File:Green_Stylish_Arrow.svg). Copyright 2015 Vitor Mazuco. CC BY-SA 4.0.

### 日本語版について

日本語への翻訳は[ohkawa](https://88171.net)によって行なわれています。この意義深いガイドの原著者であるAustin Huang氏（個人的にアドバイスも頂戴しました）、ならびにご協力いただいた皆様に深く感謝します。

日本語の翻訳文にもまた、原典（英語版）と同じく[Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)を適用します。

英語版の更新内容を日本語版にも随時反映するよう努めています。

### プライバシー {#privacy}

本サイトはGitHub Pagesでホストされているため、[GitHub Privacy Statement](https://docs.github.com/en/github/site-policy/github-privacy-statement)が適用されます。

<!--
本サイトではアクセス解析に[GoatCounter](https://goatcounter.com)を利用しています。これは[オープンソースです](https://github.com/zgoat/goatcounter)。本サイトの統計情報は[公開](https://joinmatrix.goatcounter.com)されていて（あなたがリンク先で目にする以上の情報は筆者も得られません）、[プライバシーポリシー](https://www.goatcounter.com/privacy)も確認できます。希望する場合は広告ブロッカーで`gc.zgo.at`をブロックすることで、この機能を無効化することができます。
-->

Cookieは使用していません。

### 翻訳 {#translations}

このガイドを、あなたが利用する言語に翻訳してもかまいません。ただし翻訳版が本Webサイトの承認を得るためには、以下の条件を満たす必要があります。

1. 人を思い出してください。あなたの文化圏におけるMatrixの普及のために、ベストだと思うことは*なんでも*してください。つまりこれは、一文一文の翻訳の正確さに固執する必要はないという意味です。
2. [ホームサーバ一覧](../../servers)は翻訳しないでください。代わりに、できればあなたの文化圏で利用できる公開ホームサーバの一覧を独自に作成して掲載してください。その際、文化面を考慮して一部のホームサーバの利用を*提案*してもかまいません（ただし特定のサーバの利用を*支持*することは認められません）。
3. 特定のテーマやサイトジェネレータを利用する義務はありません。私からお願いしたいのは、翻訳版がそれ単独で見やすいWebサイトを構成していることのみです。
4. 独自サブドメインの割り当てが可能な形でホストしてください（GitHub・GitLab・Gitea Pagesでかまいません）。

条件をクリアしたら、CNAMEの割り当て（言語コード`.joinmatrix.org`）を受けるために[`#public_servers:tchncs.de`](https://matrix.to/#/#public_servers:tchncs.de)で連絡してください。

## Matrixに関する質問 {#questions-about-matrix}

[matrix.org公式のFAQ](https://matrix.org/faq)も、あわせて参照してください。

### 一般的なユーザにとって、Matrixは信頼しても良いものですか？ {#for-average-users-is-matrix-trustworthy}

技術的な話ですか？はい、Matrixのほとんどのコンポーネントはオープンソースです。このガイドが唯一把握している例外は、ElementとSchildiChatがデフォルトで利用するScalarというインテグレーションマネージャです。ですがこのガイドでは、代わりに[Dimension](https://github.com/turt2live/matrix-dimension)というオープンソースのものを利用する方法を[紹介しています](../#pc-and-mobile)。

ホームサーバの運営者の話ですか？あなたには[ホームサーバ](../../servers)を選ぶ自由があることを思い出してください。大企業を信頼しますか？それともプライバシー保護に熱心な小規模グループを信頼しますか？納得できるまで調べてください。

信頼性に負の影響を与えるおそれがある唯一の要素は、Matrixが中央集権型のIDサーバ`vector.im`（`matrix.org`はこれの単なるエイリアスです）を利用することです。これはEメールアドレスを利用した連絡先検索の仕組みを提供しています。しかし2021年末時点でこの機能はオプトイン方式になっていますし、さらに言えば相手のMXIDがあればDMを送れますので、Eメールアドレスは必要ありません。

### Matrixはどのような出資を受けていますか？ {#how-is-matrix-funded}

* プロトコルの開発やmatrix.orgのホームサーバの運営を行なっているThe Matrix.org Foundation C.I.C.は、[寄付](https://matrix.org/faq/#who-and-how)（New Vectorからのものも含みます）によって運営されています。
* Elementの開発やMatrixに関連する商用サービスを提供しているNew Vector Ltdは、[投資家からの出資](https://element.io/blog/tag/investment/)を受けています。
* ホームサーバの資金源はそれぞれ異なります。寄付を受け付けているところもありますし、ビジネスの一部として運営されているものもあります。

#### イスラエルの情報機関との関係は？ {#what-about-israeli-intelligence}

もしあなたがこの陰謀論を信じてしまっているとしたら、こう考えてください。

* Matrixが多くのAmdocs従業員によって立ち上げられたことは[事実です](https://matrix.org/faq/#who-and-how)。しかしAmdocsが特定の行為に及んだとされるという理由だけで、その従業員も同じ行為に及んだと断言できるでしょうか？私たちはいつから人を勤務先で判断するようになったのでしょうか？さらに、Torはアメリカ合衆国政府から部分的に出資を受けていますが、Torに対して誰も疑問を呈さないのはなぜでしょうか？
* データ（メタデータも含みます）はルームに参加しているホームサーバの間だけで送受信されます。ホームサーバAのユーザがホームサーバBのユーザと会話しているとき、そのデータは他のどこでもない、ホームサーバAとBにのみ存在します（他のホームサーバのユーザが新たにルームに招待されるまでは）。さらに言えば、[XMPPにも同様の問題があります](https://infosec-handbook.eu/articles/xmpp-aitm/)。そして忘れてはいけないのは、あなたのデータの行方に不安があるのであれば、あなた（や、あなたの友人たち）はいつでも[自分のホームサーバを運営できる](../#set-up-your-own-homeserver-or-join-an-existing-homeserver)ということです。
* オープンなコミュニケーションプロトコルを信じ求める人々がいるからこそ、Matrixに満足な資金が集まったのです。そしてその資金が実を結んだ結果、我々は高品質なコミュニケーションプロトコルを手に入れたのです。

#### 暗号通貨関連の出資については？ {#what-about-cryptocurrency-funding}

[DiscordのNFT騒動](../matrix-vs-discord/#why-not-discord)以降、これは[よく聞かれる質問](https://www.reddit.com/r/discordapp/comments/qq4qx3/is_there_a_discord_replacement_that_doesnt/hjy61jo/?context=3)です。さて、Matrixは事実として、いくつかの暗号通貨関連企業をスポンサーに持っています。しかし、

* オープンソースプロジェクトにスポンサーの要求を満たす義務はありません。彼らはスポンサーとして謝辞を受けることはありますが、それだけです。寄付と商業上の出資は別のものだということを思い出してください。
* さらに、[Matrixは十分な資金を持っています](https://www.matrix.org/blog/2019/10/10/new-vector-raises-8-5-m-to-accelerate-matrix-riot-modular)から、特別に暗号通貨関係者の御用聞きをする必要はありません。
* さらに、Matrixのプラットフォームは非集権型ですし、Matrixのコンポーネントはオープンソースですから、
    * クライアント（たとえばElement）に暗号通貨関連の機能が組み込まれれば、即座にフォークされて巻き戻されるでしょう。
    * ホームサーバアプリケーション（たとえばSynapse）に暗号通貨関連の機能が組み込まれれば、即座にフォークされて巻き戻されるだけでなく、連合ネットワークに事実上の分断が発生する可能性があります（一部のホームサーバは追加機能を削られたバージョンを利用するでしょうが、それは機能追加されたバージョンと互換性がないかもしれません）。プラットフォームとして、これは言わば自殺行為です。

このようにたとえ出資をもってしても、コミュニティが求めないものをMatrixに組み込むのは、それを試みることすら困難でしょう。

また、あなたがどうしても、暗号通貨が開発に関わったプラットフォームの利用を拒否することにこだわるのであれば、残された選択肢はとても、とても限られたものになります。よく考えてみてください。
