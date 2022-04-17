---
title: 他のプラットフォームとの比較
layout: page-two-col
nav: false
parent: guide
permalink: guide/matrix-vs-al/
description: あなたが利用しているメッセージプラットフォームに別れを告げる時がきました。あなたを大切にする分散チャットプラットフォーム、Matrixに参加しましょう。
---

## Matrixは他のプラットフォームと比較してどうなの？ {#how-does-matrix-compare-to-other-platforms}

[これらの理由](../#why-matrix)を読んでもまだ納得できない方に向けて、このページではMatrixと既存のプラットフォームを比較していきます。ここではプラットフォームそのもののメリット・デメリットを判断するにとどめ、それらの利用人口の大小（ユーザを[箱庭](https://en.wikipedia.org/wiki/Closed_platform)に閉じ込めておくためのネットワーク効果の賜物です）については考慮しないことに注意してください。また、この比較は一般論に近いものですし、改善の提案があれば歓迎します。しかし覚えておいてほしいのは、適切にセットアップすれば他のプラットフォームとの[ブリッジ](../features/#all-about-bridges)を構築できるのがMatrixの大きな利点ということです。

話をはじめる前に、Matrixはセキュリティと社会性を併せ持っているということを思い出しましょう。他のページにこう書きました。

> 1対1のメッセージプラットフォーム（Facebookメッセンジャー、WhatsApp、iMessage、SMS…）と、協調的なメッセージプラットフォーム（Discord、Slack、Telegram…）の間で長らく待ち望まれていたのが、このMatrixです。あなたのプライバシーを適切に守りながら、同時に人々と交友を
深めることができます。

これは、プライベートな会話とオープンなグループコラボレーションを同時に実現するために、Matrix*それ自身*[^1]が一定の柔軟性を持っていることを意味します。言い換えれば、すべてに関して完璧なセキュリティを提供することを意図していないということになりますので、それをお求めなのであれば他にあたることをおすすめします。

[Discord](../matrix-vs-discord)や[Telegram](../matrix-vs-telegram)との比較は、それぞれ個別のページがあります。

### 集権化されたプラットフォーム {#centralized-platforms}

あなたがメッセージング業界で目にするほとんどのプラットフォームは、このカテゴリに属します。

これらのプラットフォームに対するMatrixの最も重要な強みは、Matrixは非集権型だということです。これは以下を意味します。

* プラットフォーム全体の運用状況を一元的に管理する主体[^2]は存在しません。
    * これにより管理主体が一方的な決定、特にユーザに痛みを強いる決定を行なうことがありません。
    * 何らかの問題（サーバダウン、買収、サービス停止）が特定のインスタンスに影響することはありますが、プラットフォーム全体の継続や安定性に影響することはありません。（一例として、[2021年10月4日のFacebookのサービス停止](https://en.wikipedia.org/wiki/2021_Facebook_outage)では一つのサーバの設定ミスによりFacebookが運営するいくつかのプラットフォームが完全にダウンしましたが、分散システムでは同様の障害は発生しません。）
* あなたは複数の主体（インスタンス）の中から信頼できるものに自分のデータを託すか、もしくは（自分のインスタンスを運営することで）あなた自身がデータを管理するかを選ぶことができます。一方で集権化されたプラットフォームではその所有者を信用する以外の選択肢は存在しません。あなたのプライベートなデータはプラットフォームに独占的に収集され、望むままの目的に利用される可能性があります。

Matrixはユーザのメッセージ内容を暗号化することができます。その一方で、

* Centralized unencrypted platforms (such as Discord, Facebook Messenger, Instagram Direct, Revolt[^3], Slack, Snapchat, Telegram cloud chats[^4], QQ and WeChat) allow unobscured access to messages by the sole owner of each platform.
* Centralized platforms that do not fully disclose details about their encryption algorithm (such as iMessage, [Line](https://citizenlab.ca/2017/08/linesecurity/), Telegram secure chats[^4], Viber[^5] and WhatsApp[^6]) cannot have their security independently verified.

Furthermore,

* Some "secure" platforms (such as Signal and WhatsApp) require you to provide a phone number or email address. Most Matrix homeservers do not require phone numbers. Depending on setup (either selfhost or with certain public homeservers), it may be possible to use Matrix without an email address as well.
* Although Signal receives widespread approval (and is probably the best centralized messaging platform in existence[^7]), its credibility continues to be subjected to ongoing debate: Its US jurisdiction, its dependence on AWS, its hostile stance towards forked clients, its delay in publishing source code, its controversial implementation of the spam detection mechanism... Whereas Matrix is [open](https://matrix.org/blog/2020/01/02/on-privacy-versus-freedom): freedom to choose jurisdiction, freedom from depending on specific third parties, freedom to choose clients, and transparency for everyone.

### Session

Session claims to be decentralized, but since the platform requires an ever-increasing amount[^8] of cryptocurrency stake for each node, running one is unreachable for most people (whereas for Matrix, there exists no such requirement from the platform), so the amount of nodes will eventually reach a finite ceiling, making it only marginally better than Signal.

### Another federated platform: XMPP

XMPP and Matrix are very similar: most of [these](../#why-matrix) also apply to XMPP. The difference is that Matrix is much *much* more intuitive for an ordinary user, whereas XMPP is far from it.

* XMPP is relatively barebone, which may not be able to serve modern communication needs.
* Clients are spread across different platforms and may support different features differently, making no client one-size-fits-all.

Furthermore, XMPP is not encrypted by default, but use of OMEMO is also quite widespread. Still, it has the same [metadata problem](https://infosec-handbook.eu/articles/xmpp-aitm/) [as Matrix](../#fn:1). However, it is true that XMPP servers are lighter than Matrix, since in XMPP, most of the heavy work is done by the clients, whereas in Matrix, the homeservers need to constantly store things.

For reference, the official comment from matrix.org is [here](https://matrix.org/faq/#what-is-the-difference-between-matrix-and-xmpp%3F).

### Peer-to-peer platforms

Platforms like Briar, Cwtch and Jami offer much more security, but at a huge cost in terms of utility due to their peer-to-peer nature, requiring participants to be online to receive messages.

## Footnotes

[^1]: これは特に、公開されたMatrixネットワークを利用する場合において成り立ちます。一部のMatrix実装（たとえばフランス政府の*Tchap*）はより強固なセキュリティを実現するために、クローズドなネットワークの利用や特定の目的のための機能拡張が行なわれていることがあります。

[^2]: ただし開発主体は除きます。しかしながら、Matrixは意思決定プロセスへのユーザの参加を拒みません。

[^3]: However, they [plan](https://github.com/orgs/revoltchat/projects/3/views/1?filterQuery=encr) to offer encryption in the undetermined future.

[^4]: Cloud chat is not encrypted in transit and is thus considered unencrypted. Secure chat uses Telegram's own MTProto protocol, comes with serious limitations on features, and is not widely used.

[^5]: Viber claims to use an encryption mechanism that is similar - but not identical - to the Signal protocol.

[^6]: Although Signal [claims](https://signal.org/blog/whatsapp-complete/) that WhatsApp is using the Signal protocol, WhatsApp's closed-source nature prevents independent verification.

[^7]: In terms of both tech and reach (hence excluding Threema).

[^8]: Relative to fiat currencies.
