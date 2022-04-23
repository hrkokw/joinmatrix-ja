---
title: MatrixとDiscordの比較
layout: page-two-col
nav: false
parent: guide
permalink: guide/matrix-vs-discord/
description: Discordを捨てるときです。ユーザが本当に大切にされるプラットフォームを想像してください。それを実現する分散チャットプラットフォーム、Matrixに参加しましょう。
---

## MatrixとDiscordの比較 {#matrix-vs-discord}

Matrixに興味をお持ちくださりありがとうございます。

MatrixはDiscordの代わりとして人気があります。しかし多くの人がその理由をまだ理解できていません。ここではまず、なぜDiscordからMatrixに移行すべきかを解説し、詳しい機能比較と役に立つヒントをご紹介します。しかしその前に、この話からはじめましょう…

## 「サーバ」という用語の妥当な定義に関する議論 {#a-discussion-on-the-proper-definition-of-server}

コンピュータ分野における「サーバ」という単語の[定義](https://en.wiktionary.org/wiki/server#Noun)を改めて見てみましょう。

> 1. A program that provides services to other programs or devices, either in the same computer or over a computer network.  
> （同一のコンピュータ内もしくはコンピュータネットワーク経由で、他のプログラムもしくはデバイスにサービスを提供するためのプログラム。）
>
> 2. A computer dedicated to running such programs.  
> （そのようなプログラムを実行するための専用のコンピュータ。）

マルチプレイヤーゲーム（たとえばMinecraft）に使われるサーバ、特定のグループのメンバーがコミュニケーションするために割り当てられるサーバ（たとえばMumbleやTeamSpeak）、そしてDiscordのボットが運用されているサーバは、いずれも前述の定義に適合します。いずれの場合も、サーバプログラム（たとえばMinecraftサーバのjarファイル）は定義の1に、サーバインフラ（たとえばVPS）は定義の2に適合します。

しかしこれはDiscordの「サーバ」には当てはまりません。それはただのデータに過ぎず、他の「サーバ」のデータと一緒に、Discordの（コンピュータという意味での）サーバに保管されています。Discordの「サーバ」はそれ自身プログラムではなく、どの「サーバ」にも専用の計算インフラが割り当てらるわけではありません[^14]ので、前述の定義のいずれにも反します。
おそらく、正しい意味での「サーバ」のイメージになじみのあるゲーマーたちの目をひきたいがために、Discordはこの技術用語の定義を汚してまで、単なるチャットグループを指す用語として使いはじめたのでしょう（だからこそDiscordはAPIドキュメントでは「サーバ」を*ギルド*と呼び分けているのです）。

### Matrixではどうなの？ {#what-about-matrix}

Matrixでは、*ホームサーバ*はサーバです。[サーバプログラムを実行するための](../#set-up-your-own-homeserver-or-join-an-existing-homeserver)（定義1）専用のインフラ（定義2）ですので、両方の定義に適合します。さらにこれらのホームサーバは、単一の存在のコントロール下にあるわけではなく個別に運用されている一方で、あらかじめ合意されたプロトコルに基づいて互いにコミュニケーション（メッセージなどの送受信）を行なうことで、Matrixプラットフォームを形成しています。このような構造を持つMatrixや[fediverse](https://fediverse.party/en/fediverse)、Eメールのようなプラットフォームは、連合型プラットフォームと呼ばれます。

## なぜDiscordではダメなの？ {#why-not-discord}

Discordについての妥当な批判はたくさん見つかるはずです。たとえば[ここ](https://cadence.moe/blog/2020-06-06-why-you-shouldnt-trust-discord)や[ここ](https://austinhuang.me/discord-issues)が挙げられます。時間があればぜひこれらにも目を通してみてください。

このガイドが扱う範囲において、DiscordからMatrixに移行すべき主な理由は、

* **プライベートなコミュニケーションにおけるプライバシーの欠如**：プライベートな会話は暗号化されていないだけでなく、積極的に検閲されています（あなたの設定によって範囲は変わりますが、フィルタリング関連の設定をすべてオフにしているにもかかわらずスキャンが行なわれることもあります）。Discordによってウイルスと判断されるようなメッセージを送信しようとしたところ、料理のレシピに置き換えられたという[報告もあります](https://www.reddit.com/r/discordapp/comments/t5v3of/viruses_now_get_turned_into_recipe_links_funny/)。
* **利用規約を遵守する限りオプトアウトの方法がないものを含む、過剰なトラッキング**：[scienceエンドポイント](https://luna.gitlab.io/discord-unofficial-docs/science.html)や（アクティビティ統計のための）プロセスロガーなどがこれにあたります[^10]。ほとんどのサードパーティークライアントはscienceエンドポイントもプロセス検知もサポートしていません。今日まで、テレメトリーデータを送信しないことを理由にバンされたユーザは報告されていません。
* **非公式クライアントやクライアントの改造に対する非友好的な姿勢**：そのためにユーザは、トラッキングや迷惑な挙動から合法的にオプトアウトすることができません。
* **電話番号の恣意的な要求**：疑わしいと判断されたり、特定の「サーバ」に参加しているユーザに対して、電話番号の確認が要求されるケースがあります。
* Discordは**ユーザのためにならない決定を行なってきました**。最近の事例では、
    * [暗号通貨の統合](https://www.reddit.com/r/discordapp/comments/qpmhs5/discord_developers_please_do_not_support_nfts/)における、偏向した協議と一方的な提案（これは激烈な反対運動を受け取り下げられました）。
    * 特定の例外[^12]を除いた、「サーバ」内のテキストメッセージの読み取りアクセスの非推奨化。これにより100を超える「サーバ」でボットを動かす場合、開発者の法的な身分証明に加えて、アプリケーションコマンドベースの対話フローが事実上強制されることになりました（これは[反対運動](https://gist.github.com/Rapptz/4a2f62751b9600a31a0d3c78100287f1)があったにもかかわらず*取り下げられませんでした*）。
* **ソースが非公開**：独立した第三者による監査を行なうことができません。
* **プライベートデータのコントロールや、信頼性の保証の欠如**：Discordは中央集権型です。[ここ](../matrix-vs-al/#centralized-platforms)も参照してください。
* **より豊かな表現力はペイウォールの向こう側**[^11]：Nitroをアンロックしたユーザは特定の追加機能を利用できます。主なものは、メッセージに何を含められるかや、2倍のギルドキャップ、2倍のメッセージサイズ制限です。
* **重要用途での利用が想定外**：Discordのスタッフから「うちの製品はただのカジュアルなチャットアプリだから」という明確な発言があったことを、ある開発者が認めています。ゲーム関係のフィギュアやおかしなミームを取り上げたマーケティングキャンペーンを見ると、このスタンスと矛盾はないように見えます。
 
[以上のすべての問題に対して、Matrixは解決策を持っています](../#why-matrix)。

### 特記事項 {#special-note}

Matrixはそのサーバーとクライアントにフリーソフトウェアを利用します。

* Discordの「スチューデントハブ」を利用しているか利用を検討している場合、組織のIT部門か学生組合にMatrixホームサーバーの設置を要求すべきです。あなたのプライバシーや組織を尊重しながら、コミュニケーションにより大きな柔軟性を得ることができます。[ドイツでは既に利用されています](https://doc.matrix.tu-dresden.de/en/why/)。
* オープンソースコミュニティは、[Discordの使用は反審美的であり差別的である](https://drewdevault.com/2021/12/28/Dont-use-Discord-for-FOSS.html)と認識すべきです。

## 用語集 {#terminologies}

### チャンネル、DMとルーム {#channel-dms-vs-room}

Discordでは、テキストメッセージがやり取りできる場のことをチャンネル（「サーバ」に属する場合）もしくはDMと呼びます。

Matrixでは、テキストメッセージがやり取りできる場のことをルームと呼びます。

### 「サーバ」とスペース {#server-vs-space}

Discordでは、DM以外のテキストチャンネル（グループDMを含む）は「サーバ」に属さねばなりません。このように、「サーバ」は特定の設定を共有するチャンネルの集合体であると理解できます。

Matrixでは、ルームはスペースに属する*ことができます*。スペースはDiscordにおける「サーバ」（属するルームの管理者らが管理）もしくは「サーバ」フォルダ（任意のユーザが管理）と似た用途で利用できます。スペースは別のスペースを含むこともできます。ルームはスペースと設定を共有することはありません。ただしルームは、スペースへの参加をルームへの参加条件とすることもできます。

## 機能比較 {#feature-comparison}

Matrixは一部の機能にペイウォールを設ける（課金を要求する）ことはありません（非集権型という性質上、そもそも不可能です）。このためDiscordでNitroもしくはNitro Classicを要求する機能は考慮の対象としません。

| 機能 | Discord | Matrix |
| --- | ------- | ------ |
| **登録** | Eメールアドレスが必要。「疑わしいアクティビティ」が検知されると電話番号を要求される可能性がある。 | ホームサーバによって異なる（特に自分で運営している場合）。**Eメールアドレスは任意の場合がある**上、電話番号は大抵の場合必須でない。登録後に*自動の*アカウント検査は行なわれない。 |
| 利用料金 | 無料。一部機能の利用には課金が必要。 | [ほとんどのホームサーバmost homeservers](../../servers)で無料（ただし寄付をぜひ検討してください）。プライベートのホームサーバを運営するにはコストがかかる場合がある（無料で可能な[場合もある](https://matrix.org/docs/guides/free-small-matrix-server)）。料金の支払い（寄付でなく）は、あなたのデータがホストされる場所とサーバ性能だけに関係し、利用できる機能に違いはないことに注意。 |
| **ユーザ名** | ユーザはディスプレイネーム（最大32文字）＋識別子（ランダムに割り当てられた4桁の数字）によって識別される。これとは別に、プログラミング用途としてユーザID（18桁前後の数字）が存在する。 | ユーザはMXID（たとえば`@alice:example.com`）で識別される。MXIDはユーザ名（ASCII文字で大文字は許されない）とサーバ名で構成される（先頭の記号と区切り文字のコロンを含め、全体で255文字まで）。ディスプレイネームを任意で追加可能（最大65200バイト）。[^7] |
| アバター | 最大8MBの静止画像。ボットを使用するかURLに直接アクセスしない限り高解像度のデータは入手できず、その場合でも最大1024×1024ピクセルに制限される。 | **添付ファイルの制限に従う。**（少なくともElementとSchildiChatでは）ズームが可能で、アップロードされたときのオリジナル解像度で表示される。アニメーション付きのアバター画像も**サポートしている**。 |
| プロフィールの説明と背景の設定 | **サポートしている**。 | 現在のところは未サポート。将来プロフィールルームとしてサポートされる予定。 |
| オフライン時のメッセージへのアクセス | 公式のWebとデスクトップのクライアントでは、リアルタイムのコネクションがない状態では意図的に一切の閲覧がブロックされる。公式のモバイルクライアントにこのような制限はない。 | クライアントにキャッシュされているメッセージは制限なく閲覧可能。 |
| プロフィールステータス | **サポートしている**。 | 事実上サポートされていない[^1]. |
| ニックネーム[^2] | サポートしている。最大32文字。 | **サポートしている** (`/myroomnick`)。最大65200バイト。 |
| 特定のアバター[^2] | Nitroが必要。 | [**サポートしている**](../features/#attachments) (`/myroomavatar`)。各種制限は添付ファイルに従う。 |
| 2要素認証 | Eメールアドレス、SMSまたはTOTP。 | ログインには不要。ただし過去の暗号化されたメッセージを読むためには特殊な認証（QRコード、絵文字列の比較、セキュリティキー）が必要。 |
| **テキストメッセージ** | 最大2000文字。Markdown（カスタムあり）をサポート。 | **最大65200バイト（フォーマット済みメッセージと、あわせて予備のプレーンテキストを送信する場合は、最大21270バイト）。[^7] [Markdownと HTMLをサポート](../features/#text)。** |
| 添付ファイル | Maximum 8 MB (maximum 100 MB for users with Nitro, and also for all users in a "server" with boost tier 3). | **Maximum 50~100 MB** (for most homeservers; customizable if you run your own homeserver). |
| Custom emotes in messages | Free users can only use static emotes defined within the "server". Using emojis from outside the "server" and using animated emojis are limited to Nitro users only. | It is possible to insert user-defined static emotes in messages, see [here](../features/#attachments). No support for animated emotes. |
| Reactions | Only emotes (Unicode or custom ones) | Unicode emotes and [text](../features/#reactions). |
| Stickers | Only stickers defined within the "server". | **Unlimited with setup.** See [here](../features/#stickers). |
| Public read receipts | Not supported. | **Supported.** |
| **Direct messages** | Not encrypted. | **Encrypted by default**, including VoIP. |
| Starting a DM | Depending on privacy settings, initiating a DM requires the two users to have established "friendship" or have certain mutual "servers." Users are given the choice to accept, remove, or report a DM (since late 2021). | Initiating a DM solely requires the recipient to accept the request[^3]. Users can leave DMs anytime they wish. |
| **Group chats** | A channel is associated with a "server." You can only join 100 "servers," 200 with Nitro. | A room is standalone, but can be optionally included and associated with a Space, which is just a room linking to other rooms. You can join **unlimited** amount of rooms. |
| VoIP in groups | Supported. | Limited Support via integration with Jitsi. Expected to be replaced by a better solution during 2022. |
| Organizing chats | "Servers" can be organized into folders, but each "server" can only belong to 1 folder. Channels in a "server" can only be organized by the "server" owner and moderators with "manage channels" permission, in a many to one fashion, and cannot be moved to another "server" once created. | Rooms can be included within an unlimited amount of Spaces. Spaces may also include other Spaces (similar to Discord's channel categories). |
| Group chat privacy | Denying "View Channel History" permission prevents users from reading messages prior to their most recent login. However the "server" owners cannot enjoy that privacy, as "server" owners cannot deny their own permissions due to how Discord's permission system works. | You may deny new members from reading messages prior to them being invited / joining. You may also allow or deny guest access (such as [Matrix Static](http://view.matrix.org/)) from reading messages. You may also enable encryption[^4]. |
| Server-side deletion guarantees | Messages that are removed from Discord are garbage collected from discord.com databases within less than 2 days.[^9] | As Matrix follows an event chain model, there is no true deletion. The closest thing available is redaction, which instructs the users and servers to blank the content but not the metadata of the event. Redactions are best-effort[^13]. |
| Publicity | Although Discord offers its own "server" discovery feature, the requirements are somewhat arbitrary, so third-party services are often used. Only "server" owners can apply to Discord's own "server" discovery directory. Third party directory services may differ. | Each homeserver has a room directory which anyone in that homeserver may publish to. |
| Invite | Through generating invite links or using an OAuth-based integration. | Through directly inviting users, or through shareable [addresses](../features/#promotion). |
| Permissions in group chats | Single-owner, up to 255 roles. How long did it take for you to learn role hierarchy?[^8] A "server" can only be shut down by its owner, and that affects everyone. Members cannot demote their own permissions. Roles of a member are reset when a member leaves hence do not survive rejoin. | Up to 2^54 power levels (-2^53 to 2^53-1, however I highly doubt you will *ever* reach that limit), with minimal permissions. A user acquires a permission if their power level is equal to or higher than the power level required for the specific permission. Rooms are not owned by any user or server, hence cannot usually forcibly be shut down without coordination. Members can demote their own permissions. Power levels of members survive leave and rejoin. |
| Size limits of group chats | 10 in group DMs, several tiers in "servers" ranging from 125 thousands to 1.5 million, subject to manual transition across those tiers.[^15] | No artificial limits, albeit current implementations do not perform well with rooms having more than a few tens of thousands of members and a few dozens of homeservers. | 
| Bans | Bans are only visible to "server" moderators. One can also see their own ban when they attempt to join a "server", but not the ban reason. | Bans are public to all members, along with the reasons. |
| Disabled and deleted account handling | Disabling an account is reversible until 2 years after disabling. Accounts that do not log in for 2 years get automatically deleted every 45 days.  Messages sent to a "server" from deleted accounts stay unless explicitly removed by somebody else. User name and user settings from deleted accounts are removed. "Servers" owned by accounts shut down by T&S may or may not stay, depending on the exact cause of the shutdown. "Servers" owned by a manually deleted account are automatically shut down. | Disabling an account is usually irreversible. Users can cause their messages to be forgotten while disabling their account: in that case, their messages are not sent to further users and servers. Rooms created by disabled accounts stay. |
| **Running a bot** | Running a bot in more than 100 "servers" requires a proof of identity, similar in manner to one encountered in international borders. Selfbotting is forbidden, but this is inconsistently enforced. | You can run bots on any user accounts[^5] [^6]. Selfbotting is permitted (but be nice). |
| **Apps to access platform** | By ToS, you are only allowed to use the official Discord app (including its PTB and Canary variants). This is not enforced consistently: some modifications and some third party clients are generally tolerated, while others may be forbidden. Third party clients that do not touch certain user profile related features tend to be not caught. | Element is the main app, but [**you're welcomed to use whatever you wish**](../#what-app-should-i-use). You can even make an app yourself[^6]! |
| **Network access** | **IPv4 only**. Users and bot developers have raised this issue repeatedly, and staff stated this is not urgent at all, despite the fact that IPv4 addresses have been exhausted worldwide: "We of course care of the future of the platform however ipv4<->ipv6 connectivity is not really going away any time soon with the availability of nat64 - and there are much more important things to work on." | **Most if not all homeservers participating in the public federation have IPv4 connectivity but IPv6 connectivity varies from homeserver to homeserver.** The biggest third party identity service, [vector.im](https://vector.im), however, is IPv4-only. |


## Helpful Tips {#helpful-tips}

* There is a [public bridge](https://t2bot.io/discord) that allows you to connect a Discord channel with a Matrix room. There is [another bridge that allows looking at your Discord direct messages from Matrix side](https://github.com/matrix-discord/matrix-appservice-discord), but that one requires self-hosting and more extensive setup than the public t2bot bridge.  (Although, backlinking Matrix data to Discord will reduce its privacy, so please take ethical concerns into account when using them.) 
* Your user colour is chosen by a hash function (varies by app) that takes in your MXID.

## Footnotes {#footnotes}

[^1]: ElementとSchildiChatではステータスが実験的機能として提供されていますが、DMの相手のみに表示されます。ステータスは暗号化されません。

[^2]: Discordでは「サーバ」、Matrixではルームです。

[^3]: Matrixに「フレンド」や「連絡先」という概念は存在しないことに注意してください（DMリストを同じ目的で利用することはできます）。しかし、Matrixではユーザのブロックを2種類の方法で行なうことができます。一つはあらゆるすべてのメッセージが受信者に届くことを防ぐ方法で、もう一つはポリシールームを無視リストとして解釈し、クライアントサイドで隠す方法です。後者は現在のところElementの実験的機能としてのみ提供されています。

[^4]: 暗号化の設定はセキュリティ上の理由から不可逆です。公開ルームで暗号化を設定することに意味はないことに注意してください。唯一の例外は、誰がメッセージを読んだかの記録を暗号学的に残す必要がある場合です。さらに暗号化の設定により、ルームへの招待を受けたか参加した時点より前のメッセージにユーザがアクセスできなくなります。

[^5]: Matrix has no distinction between user and bot accounts (nor is there any dependency between the two). Unless specifically exempted by the homeserver (not needed in most cases), bots have the same ratelimit as other users. In Element and SchildiChat, the user token of an account is available by accessing "User Settings" then "Help & About." When running an autonomous bot, please be courteous and indicate to others (in username or display name) that the account is a bot. Bots that want to control other user accounts need to create an application service, which needs to be approved by an administrator of the homeserver that the bot is using.

[^6]: あなたのアプリやボットが興味深いものでしたら、[matrix.orgにぜひ連絡をください（もしかしたらブログで紹介されるかもしれません）](https://matrix.to/#/#thisweekinmatrix:matrix.org)。

[^7]: Matrixのイベントのサイズ制限によるものです。現在の上限は65536バイトです。フォーマット済みメッセージのサイズ制限は、本文がプレーンテキストのおおよそ2倍のサイズになるだろうという想定に基づいています。

[^8]: May be more accurately described as ban hierarchy, as the order of roles only affect role changes, nick overrides, kicks and bans. Discord's permission system is otherwise "explicit allow wins".

[^9]: Somebody actually tried to report a message after deleting it and they got "no such message in our database" from T&S. Also backed by [Stanislav Vishnevskiy's blog post on infrastructure of Discord](https://blog.discord.com/how-discord-stores-billions-of-messages-7fa6ec7ee4c7#.fdhp3rxlo). However, deletions are basically a free-for-all matter: users (including bots) may decide to keep or repost deleted messages, and there is nothing stopping this.

[^10]: プロセス検知機能はデスクトップクライアントのみに存在します。とあるユーザがこの機能にリバースエンジニアリングをかけました。Steamのプロセス検知機能とは異なり、実行中の全プロセスのリストではなく、検知に成功したゲームのリストだけを送信します。ゲームアクティビティ検知のオプションをオフにすることでオプトアウトできます。scienceエンドポイントは、関係するオプションがオフにされている場合はサーバ側でデータが無視されるとされていますが、このオプションがそのとおりに機能しているかは誰も確認できていません。このため「オプトアウトできない」ものとして扱っています。

[^11]: カスタマイズや表現に関する機能にペイウォールを置くことはDiscordの主要なビジネスモデルです。これは彼ら自身が繰り返し述べていますし、多くの第三者によっても確認されている事実です。[ここ](https://seoaves.com/how-does-discord-make-money-the-discord-business-model/)や[ここ](https://moneymodels.org/business-models/how-does-discord-make-money/)を参照してください。

[^12]: The exception is messages that @-mention the bot user can still be seen without the message content event. As many bot developers said, this is still a band-aid and not a useful solution. Direct messages are not affected by message content intent. 

[^13]: Most Matrix servers are known to keep the pre-redaction content of the event for a week, while immediately sending the redaction instruction to their fellow users. Again, redactions are basically a free-for-all matter.

[^14]: More accurately speaking, guilds are mapped to the guild servers in a many-to-one fashion. This can easily be confirmed by "server" outages, which happen when the guild process in the respective server restarts or the guild is being migrated to another server. However, the end users still lack any control on choosing a particular guilds server instance to host a guild.

[^15]: Discord "servers" have an initial limit of 125000 members. "Server" owners can request this limit to be increased by filing a support ticket, in which case Discord engineering team looks at the activity of the guild and manually migrates it to a guilds server instance with a larger member limit. Known tiers are: 125k, 250k (beyond this tier, brand verification and/or partnering required), 500k, 1M, 1.5M.
