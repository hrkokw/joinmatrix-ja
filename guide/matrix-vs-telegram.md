---
title: MatrixとTelegramの比較
layout: page-two-col
nav: false
parent: guide
permalink: guide/matrix-vs-telegram/
description: Telegramを捨てるときです。ユーザが本当に大切にされるプラットフォームを想像してください。それを実現する分散チャットプラットフォーム、Matrixに参加しましょう。
---

## MatrixとTelegramの比較 {#matrix-vs-telegram}

Matrixに興味をお持ちくださりありがとうございます。ここではまず、なぜDiscordからMatrixに移行すべきかを解説し、詳しい機能比較と役に立つヒントをご紹介します。

## なぜTelegramではダメなの？ {#why-not-telegram}

このガイドの範疇では、TelegramからMatrixに移行すべき主な理由は、

* **プライベートなコミュニケーションにおけるプライバシーの欠如**：デフォルトではクラウドチャットが使われ、これはエンドツーエンドで暗号化されていません。セキュアチャットにも、デバイスを跨いだ利用ができないなど、重大な機能制限が存在します。
* **広告**：人気のチャンネルだけであるにせよ、広告が存在します。Telegramがこの制限をどうやって強制するかは誰も知りませんが、サードパーティ製のクライアントもオプトアウトすることはできません。
* **電話番号が必須です。**
* 適法なコンテンツへの介入は最小限であるとTelegramは主張しているにもかかわらず、[ロシアの政治的なボットの停止](https://en.wikipedia.org/wiki/Telegram_(software)#2021_shutdown_of_Russian_political_bots)のような**議論を呼ぶ決断**をしています。（一方でMatrixは、その非集権型という特徴から検閲が技術的に困難です。）
* **Telegramサーバのソースは非公開です。**（国家からの検閲を防ぐためだと主張していますが…？）
* **プライベートデータのコントロールや、信頼性の保証の欠如**：Telegramは中央集権型です。[ここ](../matrix-vs-al/#centralized-platforms)も参照してください。

最近の調査にもかかわらず、Telegramが独自のMTProtoプロトコルを利用している事実は依然として議論の的になっています。これをどう判断するかはあなた次第です。

## 機能比較 {#feature-comparison}

| 機能 | Telegram | Matrix |
| ---- | -------- | ------ |
| **Registration** | Requires phone number. | **Phone number is usually optional.** Depending on homeserver, **email is commonly required**. There is usually no human check after registration. |
| **Username** | Users are identified by phone number or username (if set up, 5\~32 alphanumeric characters) to fellow users, and user IDs (around 9\~10 digits) for programming purposes. A display name can be added (no limit). | Users are identified by their MXID (eg. `@alice:example.com`), composed of the username (must be ASCII characters, upper case letters are not allowed) and the server name (not exceeding 255 characters when combined, including the introducing at symbol and the colon separating the parts). A display name can be optionally added (up to ~65200 bytes)[^2]. |
| Avatar | Static or animated; limit unknown. Can be zoomed; the returned avatar has a maximum definition of 640x640. | **See "Attachments" for limits.** Can be zoomed (at least in Element/SchildiChat), in which case the avatar will be shown in the uploaded definition. Animated avatars are supported and will be rendered (at least in Element/SchildiChat). |
| Profile description | **Supported**. | Will be supported using profile rooms. Not supported currently. |
| Room-specific nicknames | Not supported, though group admins can talk on behalf of the whole group. | **Supported** (`/myroomnick`). Up to ~65200 bytes. [^2] |
| Room-specific avatars | Not supported. | [**Supported**](../features/#attachments) (`/myroomavatar`). See "Attachments" for limits. |
| 2FA | One-time token sent to another session. | Not required for login, but required (QR code, emoji verification, or Security Key) for viewing past encrypted messages. |
| **Text messages** | Maximum 4096 characters. Supports Markdown. | **Up to ~65200 bytes (up to ~21270 bytes if a formatted message with plain text fallback sent).[^2] [Supports Markdown and HTML.](../features/#text)** |
| Attachments | **Maximum 2 GB.** | Maximum 50~100 MB (for most homeservers; customizable if you run your own homeserver). |
| Reactions | Very limited. Must be enabled by group admins in groups. | All unicode emotes and [text](../features/#reactions). |
| Stickers | Up to 200 packs of 120 static or 50 animated each. | **Unlimited (static or animated) with setup.** See [here](../features/#stickers). |
| Public read receipts | Supported ambiguously. | **Supported.** |
| **Direct messages** | Not encrypted unless explicitly opted into secret chat, which cannot be carried across devices. VoIP is encrypted. | **Encrypted by default**, including VoIP. |
| **Group chats** | You can join up to 500 groups and channels. | You can join an **unlimited** amount of rooms. |
| VoIP in groups | Supported. | Limited Support via integration with Jitsi. Expected to be replaced by a better solution during 2022. |
| Organizing chats | You can pin or archive groups (similar to favourite and low priority on Element/SchildiChat). | Rooms can be included within an unlimited amount of Spaces. Spaces may also include other Spaces. |
| Group chat privacy | You may deny new members from reading more than 100 messages prior to them joining. | You may deny new members from reading messages prior to them being invited / joining. You may also allow or deny guest access (such as [Matrix Static](http://view.matrix.org/)) from reading messages. You may also enable encryption[^1]. |
| Publicity | Any group or channel set to public can be listed in search results, but how they are shown is arbitrary, as global search is not always visible to users. | Each homeserver has a room directory which anyone in that homeserver may publish to. |
| Invite | Through directly inviting users, or through generating invite links. | Through directly inviting users, or through shareable [addresses](../features/#promotion). |
| Group chat permissions | Permissions of each administrator are set manually. All admins are equal (except owner). Permissions of a member do not survive leave and rejoin. | 2^54 power levels (I think it's -2^53 to 2^53-1, however I highly doubt you will *ever* reach that limit). A user acquires a permission if their power level is equal to or higher than the power level required for the specific permission. Power levels of members survive leave and rejoin. |
| Size limits of group chats | Up to 100k members in groups, unlimited in one-to-many channels. | No artificial limits, albeit current implementations do not perform well with rooms having more than a few tens of thousands of members and a few dozens of homeservers. | 
| Disabled and deleted account handling | Disabling an account is reversible until one year after disabling. Accounts that do not login for a year get automatically deleted. Messages from deleted accounts survive for one more year from deletion. | Disabling an account is usually irreversible. Messages from disabled accounts are not sent to further users and servers. Rooms created by disabled accounts stay. |
| Ads | Popular channels now carry ads that you cannot opt out. | It is technically possible for a homeserver to insert ads, but **there are no known occurrences**. |
| **Network access** | **IPv4 supported, [IPv6 broken](https://flameeyes.blog/2017/08/06/ipv6-horror-story-telegram/)**.  | **Most if not all homeservers participating in the public federation have IPv4 connectivity but IPv6 connectivity varies from homeserver to homeserver.**. |


## 役立つヒント {#helpful-tips}

TelegramグループとMatrixルームを接続できる[ブリッジ](https://t2bot.io/telegram)が存在します。

## 脚注 {#footnotes}

[^1]: 暗号化の設定はセキュリティ上の理由から不可逆です。公開ルームで暗号化を設定することに意味はないことに注意してください。唯一の例外は、誰がメッセージを読んだかの記録を暗号学的に残す必要がある場合です。さらに暗号化の設定により、ルームへの招待を受けたか参加した時点より前のメッセージにユーザがアクセスできなくなります。

[^2]: Matrixのイベントのサイズ制限によるものです。現在の上限は65536バイトです。フォーマット済みメッセージのサイズ制限は、本文がプレーンテキストのおおよそ2倍のサイズになるだろうという想定に基づいています。
