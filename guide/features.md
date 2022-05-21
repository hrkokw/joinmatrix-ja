---
title: Matrixの特徴についてもっと詳しく
layout: page-two-col
nav: false
parent: guide
permalink: guide/features/
description: あなたを大切にする分散チャットプラットフォーム、Matrixのさまざまな特徴について。
---

## Matrixの特徴についてもっと詳しく {#more-features-of-matrix}

もう[基本](..)は押さえられたと思いますので、Matrixのさまざまな特徴に関して込み入ったお話をしましょう。
あなたがある程度の下調べをしているだろうこと、その上であまり直感的でない特徴について知りたいと思ってこのガイドをお読みになっているという前提で話を進めていきます。

## チャットについてのすべて {#all-about-chatting}

<div class="flash flash-warn">
  <strong>重要！</strong> Matrixのユーザ名を後から変更することはできません。よく考えてから決めましょう。
</div>


### メッセージ {#messages}

<div class="flash flash-warn"><ul>
  <li>投稿後に編集されたメッセージは、オリジナルのメッセージに加えて<b>すべての<b>編集内容を削除しないと、完全に削除したことにはなりません。</li>
  <li>仕様の欠陥によって、メッセージの最初のリビジョン（編集版）はオリジナルと一緒にしか削除できません。その後に続くリビジョンは個別に削除できます。</li>
  <li>リプライがついたメッセージは、オリジナルのメッセージに加えて<b>すべての</b>リプライが削除されないと、完全に削除したことにはなりません。</li>
  <li>あなたのメッセージを読むことができる人は、メッセージが削除される前にコピーを取っているかもしれません。（さらにメッセージが暗号化されていない場合、ホームサーバの運営者もそれが可能です。）これは事実上<i>あらゆる</i>インスタントメッセージプラットフォームに当てはまりますので、あなたが発言する内容にはいつも注意しましょう。</li>
  <li>迷惑行為をするようなユーザがいれば、あなたの側で無視設定をすることができます。間違って<a href="https://github.com/vector-im/element-web/issues/12394">自分を無視しないように！</a></li>
</ul></div>

#### テキスト {#text}

メッセージの冒頭に`/html`と書かない限り、MatrixはMarkdownによるマークアップをサポートしています。[CommonMark仕様](https://commonmark.org/help/)のすべてに対応していますが、

* 画像を貼り付ける場合、リンクはHTTP/SのURLではなく[MXC URI](#attachments)でなければなりません。これはMatrixの仕様で定められていて、仕込まれたIPトラッカーでユーザがトラッキングされることを防ぐための制限です。
* コードブロックの書式ハイライトがサポートされています。最初の3つのバッククオートの直後に言語を指定してください。

さらにこれらに加えて、

* 打ち消し線は、ElementとSchildiChatでは`<del>テキスト</del>`（`/html`はなし）、FluffyChatでは`~~テキスト~~`を使ってください。
* 下線は、ElementとSchildiChatでは`<u>テキスト</u>`（ここでも`/html`はなし）、FluffyChatでは`__テキスト__`です。
  * これらの違いはメッセージを書くときだけのものです。どちらのクライアントも投稿されたメッセージは同じように表示します。
* ネタバレを隠すには、
  * ElementとSchildiChatでは、メッセージを`/html`から書きはじめて、好きな位置に以下のいずれかの行を追加します。これによって`ネタバレの内容`を隠し、一つめの場合は代わりに`理由`を表示することができます。理由なしにメッセージ全体をネタバレの内容にしたい場合は、`/html`の代わりに`/spoiler`でメッセージを書きはじめるだけでOKです。
  ```html
  <span data-mx-spoiler="理由">ネタバレの内容</span> # 理由あり
  <span data-mx-spoiler>ネタバレの内容</span> # 理由なし
  ```
  * FluffyChatでは、`||理由|ネタバレの内容||`で同じことが実現できます。
* テーブル（表）はHTMLでのみ実現できます（後述）。

And, about slash commands on Element and SchildiChat on PC related to text messages:

* Matrix also supports [these HTML tags](https://spec.matrix.org/v1.1/client-server-api/#mroommessage-msgtypes) if you prefix a message with `/html`.
* Prefixing your message with one of the following commands will trigger the corresponding visual effect for all Element/SchildiChat users on PC who are currently focused on the room: `/confetti`, `/fireworks`, `/rainfall`, `/snowfall` and `/spaceinvaders`. The effect will only be triggered once for these users only.
* Prefixing your message with `/me` will cause your message to start with `*` followed by your display name[^1].
* Prefixing your message with `/rainbow` will make the text appear in rainbow colours.
  * The two commands above can be combined using `/rainbowme`.
* Prefixing your message with `/shrug`, `/tableflip`, `/unflip` and `/lenny` will place the corresponding ASCII emote at the **beginning** of the message content. (This differs from Discord, where the emote is placed at the end.)

#### Attachments {#attachments}

You can upload files onto messages. The size limit varies by the homeserver you're on, but most homeservers have it between 50 and 100 MB. There are no restrictions for file types, allowing some apps to offer the ability to record and send voice messages.

All files you upload onto Matrix are assigned an [MXC URI](https://spec.matrix.org/v1.1/client-server-api/#matrix-content-mxc-uris), which you can use for referencing to the corresponding file. The MXC URI can be retrieved with the following steps:

1. Find the message.
2. On Element and SchildiChat on PC, hover over the message and click the three dots. On FluffyChat, long press the message and click the three dots on the top.
3. "View Source."
4. Under the `content` JSON object, locate the `url` attribute. The URI the starts with `mxc://` is the MXC URI.

If the attachment is an image, the URI allows you to do the following, at least on Element and SchildiChat:

* Change your avatar for the current room using `/myroomavatar mxc://...`
* Embed the image on text messages by inserting `![alt text](mxc://...)` (You can also use `<img>` tags under `/html`)

![Embedding an image](../../assets/images/embed.png)

The attachment can be accessed on the internet by replacing the `mxc://` prefix with `https://$SERVER/_matrix/media/r0/download/`, where `$SERVER` is the domain of *any* homeserver (it does not need to be in the room).

<div class="flash flash-warn">
  The attachments themselves can only be deleted by the homeserver operator, and until then, they are visible to the public. This means, especially, that deleting a message will <b>NOT</b> delete its attachments! (However, attachments uploaded in an encrypted room are visible to the public in the encrypted form, where only its intended recipients have the keys to decrypt it.)
</div>
<div class="flash">
  It is possible to use "custom emojis/emotes" in text messages by embedding the emote: simply adjust the image, upload it in an unencrypted room, get its MXC URI, and place the embedding code in messages. Furthermore, FluffyChat allows you to assign a <code>:shortcode:</code> to custom emotes so that they can be entered like normal emotes: Go to user settings, then "Conversations", then emoji settings. Note that embed GIFs will not animate.
</div>

#### Stickers {#stickers}

Currently, support for stickers across Matrix is somewhat inconsistent. Note that stickers sent from either app are visible to both apps.

* For Element and SchildiChat, stickers are offered by integration managers. If you have used [the config](../#pc-and-mobile) provided by this guide, the [Dimension integration manager](https://dimension.t2bot.io) allows you to create your own sticker packs.
* For FluffyChat, stickers are offered by rooms, some of them are collected in the [`#stickers-and-emojis:pixie.town`](https://matrix.to/#/#stickers-and-emojis:pixie.town) Space. To get stickers or custom emotes in a room, press the room name, expand settings, and open emoji settings. Then, open the desired sticker or emote pack and enable them as you wish.

See [here](https://1hiking.github.io/posts/2021/09/matrix-stickers/) if you want more details.

### Reactions {#reactions}

You may react to any message with any unicode emoji or any plaintext content[^2]. The latter is available...

* On FluffyChat, by replying to a message and entering the desired text prefixed with `/react` in the composer;
* On SchildiChat, by clicking the reaction picker for a message, entering the desired text in the search box, and then choosing "React with (text)."

### Voice/Video calling {#voicevideo-calling}

Voice/video calling is currently only supported for private messages (rooms with only 2 participants).

Currently, if you try to start a call in a room with more than 2 participants, a [Jitsi Meet](https://meet.jit.si) (not part of Matrix) [widget](#integrations) will be displayed for all users as a temporary solution. However, work is underway to allow native voice/video calling for groups, which hopefully will be enabled [by early 2022](https://matrix.org/blog/2021/12/22/the-mega-matrix-holiday-special-2021#native-matrix-videovoip-conferencing).

## All about bridges {#all-about-bridges}

Matrix prides itself in technical interoperability, i.e. ability to work with other platforms. Therefore, Matrix allows you to connect your chats to another platform.

Note that encryption is **not** supported on most bridges. Furthermore, the following instructions apply across the Matrix federation, but private homeserver providers as well as some public homeservers operate certain bridges for the benefit of their users, in which case please inquire the relevant providers.

<div class="flash flash-warn">
 Some bridges offer the possibility to bridge an account from another platform onto Matrix (known as puppeting). However, it is often against the ToS of the platform to do so (as interoperability is antithetical to centralized "walled garden" approaches) and may result in loss of account. Furthermore, it may damage the encryption mechanisms of the platform, as messages must be decrypted first before re-encryption. Lastly, the bridge operator can see your login credentials (not an issue if you're hosting the bridges yourself). You have been warned.
</div>

### Discord {#discord}

To bridge a Matrix room with a Discord channel, you can install [matrix-appservice-discord](https://github.com/Half-Shot/matrix-appservice-discord) if you're running your own homeserver[^3], or set up one of the free public bridges otherwise:

* [t2bot](https://t2bot.io/discord)
* [tchncs.de](https://tchncs.de/matrix)
* [TeDomum](https://tedomum.net/service/matrix/bridges/)

Matrix users will show up as webhooks on Discord, and Discord users will show up as standard users on Matrix (but you cannot DM them). There is no puppeting.

### Telegram {#telegram}

To bridge a Matrix room with a Telegram group chat, you can install [mautrix telegram](https://github.com/mautrix/telegram) if you're running your own homeserver, or set up one of the free public bridges otherwise:

* [t2bot](https://t2bot.io/telegram) (No puppeting)
* [tchncs.de](https://tchncs.de/matrix) (Puppeting requires approval)
* [TeDomum](https://tedomum.net/service/matrix/bridges/)
* [SNT](https://syscom.utwente.io/info/matrix/telegram/)

When a Matrix room is bridged with a Telegram group, Matrix users will be represented by the bridging bot on Telegram, while Telegram users will show up as standard users on Matrix (but you cannot DM them). When you log into a Telegram account on a bridge, you may use it to control your own account such that you may interact with the whole of Telegram from Matrix.

### Slack {#slack}

To bridge a Matrix room with a Slack channel, do the following on Element or SchildiChat on PC:

1. In your desired room, click the info button on the top-right.
2. "Add widgets, bridges & bots"
3. Navigate to "Slack bridge" and follow the instructions.

### IRC {#irc}

You can join any IRC channel on [these networks](https://matrix-org.github.io/matrix-appservice-irc/latest/bridged_networks) directly from Matrix. Matrix users will show up in their display name, suffixed with `[m]`.

<div class="flash flash-warn">
  You <i>can</i> register the nickname, but your NickServ password would be visible to your homeserver as encryption is not supported for bridges, so do so at your own risk.
</div>

### XMPP {#xmpp}

You can join any XMPP MUC on any instance directly from Matrix, using the Bifrost bridge provided by [matrix.org](https://github.com/matrix-org/matrix-bifrost/wiki/Address-syntax) or [aria-net.org](https://aria-net.org/SitePages/Portal/Bridges.aspx).

### Other {#other}

Matrix supports many other platforms, but such bridges generally require setup. If you want to bridge those platforms, or if you have performance requirements that cannot be met by existing public bridges, you may either:

* [Host the bridges yourself](https://matrix.org/bridges/), if you run your own homeserver
* Use public bridges (which you're encouraged to donate for):
  * [Aria Network](https://aria-net.org/SitePages/Portal/Bridges.aspx) (Facebook, Instagram, MS Teams, Twitter, WhatsApp; only available to accounts on the aria-net.org homeserver)
  * [yatrix.org](https://yatrix.org/#interoperabilität) (Signal, WhatsApp; requires approval)
  * [TeDomum](https://tedomum.net/service/matrix/bridges/) (WhatsApp)
* Set up bridges as part of a managed homeserver hosting:
  * [Element Matrix Store](https://element.io/element-matrix-store) (WhatsApp, Slack, MS Teams, IRC, Discord, Telegram)
  * [etke.cc](https://etke.cc) (Many platforms)
  * [ungleich](https://ungleich.ch/u/products/hosted-matrix-chat/) (Many platforms)
* Purchase managed bridging services without a homeserver:
  * [Element One](https://element.io/element-one) (WhatsApp, Signal, Telegram)
  * [Beeper](https://www.beeper.com/) (Many platforms; has waitlist)

## All about rooms {#all-about-rooms}

Because FluffyChat's room management capabilities are somewhat limited by design, this guide will base this section upon Element and SchildiChat on PC.

### Promotion {#promotion}

If you want to promote a public room, you can publish public addresses and/or place it on your homeserver's [room directory](../#what-rooms-can-i-join).

To publish an address:

1. Go to room settings.
2. In the "General" tab, under "Room Addresses" there is "Local Addresses." As indicated, you can only create addresses on the homeserver you are on[^4].
3. Enter the localpart (the part before `:`) of your desired address and then click "Add".
4. Under "Published Addresses," enter the entire address (with homeserver domain), then click "Add".
5. The "Main Address" is used for room directories and for mentioning the room in other rooms. Select one from the published addresses.
6. If you want to advertise your room in your homeserver's[^4] room directory, enable "Publish this room to the public in (server)'s room directory?"

Steps 1 to 3 can be done by anyone, whereas step 4 by 6 requires the user to have a power level equal to or higher than the required level for "Change main address for the room."

A public address also allows you to [link the room from a webpage](https://matrix.to/).

### Moderation {#moderation}

See [the official guide](https://matrix.org/docs/guides/moderation#moderating-rooms) (just the linked section).

<div class="flash flash-warn">
  If you promote a user to the same power level as you, then you will <b>not</b> be able to demote them!
</div>
<div class="flash">
  It is a good idea to copy ACLs of other rooms (especially those of popular public rooms) and use them on your own to strengthen your room's defense to unwanted content. To do so:
  <ol>
    <li>Enter <code>/devtools</code> in the room you want to copy ACL from.</li>
    <li>Click "Explore Room State."</li>
    <li>Click <code>m.room.server_acl</code>.</li>
    <li>Click "Edit."</li>
    <li>Copy the content in the box. (It is futile to try to hit "Send" as you probably don't have the permission to.)</li>
    <li>Repeat steps 1 to 4, this time in the room you want to use the copied ACL in.</li>
    <li>Paste the content in the box and hit "Send."</li>
    <li>Confirm success. A state event will be created in the room, indicating that you have changed the ACL.</li>
    <li>Note that denying a homeserver whose users are already present in a room will not automatically kick the users. If necessary, enter the homeserver domain in the search box of the member list and kick them from your room. They will not be able to join back.</li>
  </ol>
</div>
<div class="flash">
  You <a href="https://github.com/matrix-org/mjolnir/issues/165">cannot</a> selfhost <a href="https://github.com/matrix-org/mjolnir">mjolnir</a> without permission to go over ratelimit for the homeserver the bot is on. This means, that you may selfhost it if you run your own homeserver, or consult your homeserver operators otherwise (they may be hosting it already).
</div>

### Integrations {#integrations}

Integrations in Matrix include widgets and bots.

Widgets display an interactive HTML page on top of chat messages. This only works on Element and SchildiChat on PC. You can use the `/addwidget` command, or the "Add widgets, bridges & bots" link in the room info sidebar. Note that individual members must opt into displaying the widget, and can choose to dismiss ("unpin") the widget for themselves at any time. Furthermore, anyone with power level above the required level for "Modify Widgets" will be able to dismiss ("unpin") the widget for everyone in the room.

Bots perform automated actions (like sending messages). [maubot](https://github.com/maubot/maubot) is the only well-known self-hostable bot, containing a variety of plugins. [t2bot.io](https://t2bot.io/) as well as some homeservers host certain plugins for public use.

[Bridges](#all-about-bridges) are also bots, but some bridges need to create new accounts to serve as puppets, which should only be operated on a homeserver that you own or otherwise have permission to run such bots on.

## Footnotes {#footnotes}

[^1]: Similar to the eponymous command in Minecraft.

[^2]: Unlike Instagram Direct, where doing so will actually overflow the screen (you can try it but it will involve reverse engineering), Matrix apps handle this properly by showing the first few (≈10) characters followed by ellipsis. It seems to be mostly intended to be used by bots, as seen in [This Week in Matrix](https://matrix.to/#/#thisweekinmatrix:matrix.org), but since most bots are no different from other users, humans are welcomed to use it too.

[^3]: If you're running your own bridge, please manually incorporate [this pull request](https://github.com/Half-Shot/matrix-appservice-discord/pull/704) to support parsing Discord replies. (The t2bot bridge incorporates it since December 2021.)

[^4]: If you want addresses or/and publicity on other homeservers, you can create accounts, join the room, and do these steps. But be nice and don't spam. Remember, homeserver operators *can* remove your room from the room directory or even prevent anyone on their homeservers from joining your room.
