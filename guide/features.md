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

* 打ち消し線は、Element・SchildiChatでは`<del>テキスト</del>`（`/html`はなし）、FluffyChatでは`~~テキスト~~`を使ってください。
* 下線は、Element・SchildiChatでは`<u>テキスト</u>`（ここでも`/html`はなし）、FluffyChatでは`__テキスト__`です。
  * これらの違いはメッセージを書くときだけのものです。どちらのクライアントも投稿されたメッセージは同じように表示します。
* ネタバレを隠すには、
  * Element・SchildiChatでは、メッセージを`/html`から書きはじめて、好きな位置に以下のいずれかの行を追加します。これによって`ネタバレの内容`を隠し、一つめの場合は代わりに`理由`を表示することができます。理由なしにメッセージ全体をネタバレの内容にしたい場合は、`/html`の代わりに`/spoiler`でメッセージを書きはじめるだけでOKです。
  ```html
  <span data-mx-spoiler="理由">ネタバレの内容</span> # 理由あり
  <span data-mx-spoiler>ネタバレの内容</span> # 理由なし
  ```
  * FluffyChatでは、`||理由|ネタバレの内容||`で同じことが実現できます。
* テーブル（表）はHTMLでのみ実現できます（後述）。

そして、PC版Element・SchildiChatのテキスト関連のスラッシュコマンドについて、

* メッセージを`/html`で書きはじめると、Matrixは[これらのHTMLタグ](https://spec.matrix.org/v1.1/client-server-api/#mroommessage-msgtypes)をサポートします。
* 以下のスラッシュコマンドをメッセージ冒頭に置くことで、そのルームにPC版Element・SchildiChatでアクセスしているユーザに対してエフェクトを表示することができます：`/confetti`（紙吹雪）、`/fireworks`（花火）、`/rainfall`（雨）、`/snowfall`（雪）、`/spaceinvaders`（スペース・インベーダー）。これらのエフェクトは各ユーザに一度だけ表示されます。
* `/me`ではじめると、メッセージが`*`と表示名ではじまります[^1]。
* `/rainbow`ではじめると、テキストが虹色で表示されます。
  * 上記の2コマンドは、`/rainbowme`で組み合わせることができます。
* `/shrug`（肩をすくめる）、`/tableflip`（ちゃぶ台返し）、`/unflip`（ちゃぶ台戻し）、`/lenny`（&#x1F60F）は、それぞれ対応するASCIIアートをメッセージの**冒頭に**表示します。（Discordでは末尾に表示されますが、それとは異なります。）

#### 添付ファイル {#attachments}

メッセージにはファイルを添付することができます。サイズ制限はあなたが利用しているホームサーバによって異なりますが、ほとんどのホームサーバでは50〜100MBであることが多いです。ファイル形式の制限はなく、アプリによっては音声を録音して送ることもできます。

Matrixにアップロードされたファイルには必ず[MXC URI](https://spec.matrix.org/v1.1/client-server-api/#matrix-content-mxc-uris)が割り当てられ、そのファイルを指し示すのに使うことができます。MXC URIは以下の手順で確認することができます。

1. メッセージを探します。
2. PC版Element・SchildiChatでは、メッセージにカーソルを持っていき三点メニューをクリックします。FluffyChatでは、メッセージを長押しして先頭に表示される三点メニューをクリックします。
3. "View Source"（ソースを表示）を選択します。
4. `content`（内容）に表示されるJSONオブジェクトから、`url`属性を探します。この`mxc://`ではじまるURIがMXC URIです。

添付ファイルが画像である場合、少なくともElement・SchildiChatではMXC URIを使って以下のことができます。

* `/myroomavatar mxc://...`で、現在のルームでのあなたのアバターを変更することができます。
* `![説明テキスト](mxc://...)`でメッセージに画像を貼り付けることができます（`/html`の場合は`<img>`タグで同じことができます）。

![画像の貼り付け](../../assets/images/embed.png)

添付ファイルは、MXC URIの`mxc://`の部分を`https://$SERVER/_matrix/media/r0/download/`に置き換えると、たとえば普通のWebブラウザなどでアクセスすることができます。このとき`$SERVER`は*いかなる*ホームサーバのドメインでも構いません（ルームに参加している必要もありません）。

<div class="flash flash-warn">
  添付ファイルはホームサーバの運営者だけが削除でき、それまではインターネット上に公開された状態にあります。つまり、メッセージを削除したらその添付ファイルも自動的に削除される、ということは<b>ありません！</b>。（ただし暗号化が有効なルームにアップロードされたファイルは、暗号化された状態で公開されます。このため正当な鍵を持っている人だけが元の内容を見ることができます。）
</div>
<div class="flash">
  画像を用意して暗号化されていないルームにアップロードし、MXC URIを確認してメッセージに貼り付けるという方法で、オリジナルの絵文字やエモートを使うことができます。さらにFluffyChatでは、オリジナルのエモートに<code>:名前:</code>を割り当てることができ、普通のエモートと同じように使うことができます。ユーザ設定から"Conversations"（会話）の絵文字設定を確認してください。GIFを添付してもアニメーションはしないことに注意してください。
</div>

#### ステッカー {#stickers}

現在のところ、Matrixにおけるステッカーのサポートは一貫していません。どちらかのアプリから送られたステッカーは両方のアプリで見ることができます。

* Element・SchildiChatでは、ステッカーはインテグレーションマネージャによって提供されます。このガイドの[設定](../#pc-and-mobile)を使うと、[Dimension integration manager](https://dimension.t2bot.io)で独自のステッカーパックを作ることができます。
* FluffyChatでは、ステッカーはルームから提供されます。そのうちいくつかは[`#stickers-and-emojis:pixie.town`](https://matrix.to/#/#stickers-and-emojis:pixie.town)スペースにまとめられています。ルームにステッカーやカスタムエモートを追加するには、ルーム名をクリックし、設定から絵文字設定を開いて、好きなステッカーやエモートパックを有効化してください。

より詳しく知りたい場合は[ここ](https://1hiking.github.io/posts/2021/09/matrix-stickers/)を参照してください。

### リアクション {#reactions}

あらゆるメッセージに、Unicode絵文字かテキスト[^2]でリアクションすることができます。後者を使うには、

* FluffyChatではメッセージへの返信モードに入り、`/react`のあとにテキストを入力します。
* SchildiChatではメッセージへのリアクション選択を呼び出し、検索欄にテキストを入力して"React with (テキスト)"を選択します。

### 音声・ビデオ通話 {#voicevideo-calling}

音声・ビデオ通話は現在のところプライベートメッセージ（参加者が2人だけのルーム）だけでサポートされています。

現在、3人以上が参加しているルームで通話を開始しようとすると、一時的な回避策として[Jitsi Meet](https://meet.jit.si)（Matrixの一部ではありません）の[ウィジェット](#integrations)が表示されます。しかしMatrixネイティブのグループ通話を実現する取り組みが進んでいて、[2022年初頭まで](https://matrix.org/blog/2021/12/22/the-mega-matrix-holiday-special-2021#native-matrix-videovoip-conferencing)に実現することが期待されています。

## ブリッジについてのすべて {#all-about-bridges}

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
