---
title: Join Matrix! ガイド
ntitle: ガイド
layout: page-two-col
nav: true
parent: guide
permalink: guide/
description: あなたを大切にする分散チャットプラットフォーム、Matrixの初心者向けガイド
---

## Join Matrix! ガイド: はじめに

ようこそ！このWebサイトはMatrix（たまにElementと[間違われます](#matrixそれともelement)が）の初心者向けのガイドとなることを目指しています。Matrixは、既存の集権的な商用プラットフォームの代替となることを目指す、オープンな分散コミュニケーションプロトコルです。ただこの説明はちょっと大仰で、逆に人々を混乱させがちです。なのでこのガイドでは、チャットという観点でより簡単な言葉を使った説明を心がけています。まず「なぜ？」から始めて「どうやって？」に話を進めていきます。このパートはまだMatrixを使ったことがない人に向けた内容です。より深い情報をお探しの場合はサイドバーを見てみてください。

## なぜMatrixなの？

1対1のメッセージプラットフォーム（Facebookメッセンジャー、WhatsApp、iMessage、SMS…）と、協調的なメッセージプラットフォーム（Discord、Slack、Telegram…）の間で長らく待ち望まれていたのが、このMatrixです。あなたのプライバシーを適切に守りながら、同時に人々と交友を深めることができます。他のプラットフォームと比較したときにMatrixが秀でるメリットは、大まかに2つ挙げることができます。

* **自由。** どのようにプラットフォームを使い、あなたのデータがどのように扱われるかは、あなた自身が決められるべきです。
    * 会話はエンドツーエンドで暗号化できます[^1]。これはダイレクトメッセージ・グループメッセージの両方でデフォルトで有効化されます。
    * 収集される情報は最低限です。アドレス帳の同期はされません[^3]し、登録のときに「あなたは人間ですか？」のチェックもありません。電話番号の提供は任意ですし、Eメールアドレスの提供すら任意です（選んだホームサーバによります）。
    * あなた自身がサーバを運用できます。もしくは、あなたが選んだ[パブリックなホームサーバ](../servers)に参加することもできます。どちらの方法でも、Matrixネットワーク上でのあなたの立場は変わりません。[^4]
    * [ブリッジ](./features/#all-about-bridges)を使って、他のプラットフォーム上のユーザとチャットすることができます。Matrixに移るための手間は最小限ですみます。
    * Matrixはオープンなプロトコルであるため、チャット以外の目的にも拡張することができます。たとえば[ヘルプデスク](https://www.safesupport.chat/)、[ソーシャルメディア](https://minestrix.henri2h.fr/), リアルタイムな共同作業など…
* **信頼。** あなたは使うソフトウェアを心から信頼できるべきです。
    * Matrixはオープンなプロトコルであり、その[アプリ](#what-app-should-i-use)やサーバ[^6]のほとんど[^5]がオープンソースです。あなたが貢献することもできます。
    * MatrixはEメールと同じく分散型です。従来の[集権的](./matrix-vs-al/#centralized-platforms)なプラットフォームと異なり、何らかの単一の存在がMatrixネットワークをコントロールしているわけではありません。それぞれ独立して稼働するホームサーバが、定められたプロトコルに従って互いにコミュニケートしています。
    * さらに、個々のホームサーバはダウンする可能性がありますが、Matrixネットワーク全体がオフラインになることは**ありえません**。
    * 新しいアプリを作ったり提案を[出したりレビューしたり](https://spec.matrix.org/unstable/proposals/)することで、Matrixの改善に関わることができます。あなた自身の手で、プラットフォームをより良い方向へ導くことができます。
    * Matrixは公共機関、特にドイツ（[ヘルスケア](https://matrix.org/blog/2021/07/21/germanys-national-healthcare-system-adopts-matrix)、[軍](https://element.io/case-studies/bundeswehr)、[大学](https://doc.matrix.tu-dresden.de/en/why/)）や[フランス](https://element.io/case-studies/tchap)の機関から支持されています。

そしてもちろんMatrixは、クロスプラットフォーム、リアルタイム性、使いやすさなど、現代のメッセージプラットフォームが持つすべての機能を備えています。ただそれよりも重要なのは、**あなたを大切にする**良識あるチャットプラットフォームが**存在しうる**ことをMatrixが体現していることなのです。

ここまでの説明で納得できなければ、[Discord](./matrix-vs-discord)や[Telegram](./matrix-vs-telegram)といった他のプラットフォームと[Matrixを比較](./matrix-vs-al)してみてはいかがでしょう？

<div class="flash">
  Matrixは完璧ではありませんが、日に日に改善されています。<a href="https://matrix.org/blog/posts">The Matrix.org blog（英語）</a>をフォローして、Matrixに関するニュースにアクセスしましょう。
</div>

## はじめる

Matrixを試す準備ができましたか？それでは、先へ進みましょう。

### Matrix？それともElement？

* Matrixとは、イギリスを本拠地とする非営利団体、[The Matrix.org Foundation C.I.C.](https://matrix.org/foundation/)が開発しているプロトコルです。同時に、すべてのユーザやルームを含むMatrixネットワーク全体を指すこともあります。
* Element（過去にはRiot.imという名前でした）とは、イギリスを本拠地とする営利団体、[New Vector Ltd](https://element.io/about)が開発するMatrixの代表的なアプリです。同時に、同企業が提供する[Element Matrix Services](https://element.io/matrix-services)のような商用サービスを指すこともあります。

[この後にも触れます](#what-app-should-i-use)が、ElementはMatrixにアクセスするアプリの一つにすぎません。ですから、このプラットフォームを単に「Matrix」と呼ぶのが正しいです。しかしあなたがそれを*[マトリックス](https://en.wikipedia.org/wiki/The_Matrix)*と呼んでも誰も止めません。

### 自分でホームサーバを作るか、すでにあるホームサーバに参加するか

もしもあなたが満足なインフラと、インターネット上にサービスを公開する技術スキルをお持ちなのであれば、自分のホームサーバを作ることにチャレンジできます[^6]。現在、もっとも普及しているホームサーバは[Synapse](https://github.com/matrix-org/synapse/)です。[インストール方法](https://matrix.org/docs/guides/installing-synapse)をご覧ください。[Oracle Cloud](https://matrix.org/docs/guides/free-small-matrix-server)を使って無料でホームサーバを作ることもできるかもしれません。

しかし、多くの人にとって必ずしも望ましい選択ではないかもしれません。その場合は次の選択肢があります。

* [公開ホームサーバ一覧](../servers)から選んだ既存のホームサーバに参加する
* ホームサーバを運営している友人に連絡してみる
* 有償の[ホスティングサービス](https://matrix.org/hosting/)を契約する

<div class="flash">
  いわゆる「標準」のMatrixホームサーバは<code>matrix.org</code>で、<a href="https://matrix.org/blog/2020/01/02/on-privacy-versus-freedom">2020年の推計</a>では全Matrixユーザの35%が利用しています。それを利用するのも悪くはありません（Matrixをすぐに試すことができますし）。しかし将来に渡ってMatrixを利用するつもりであれば、他のホームサーバの利用（自分で運営することも含めて）を強くお勧めします。Matrixプロトコルが提唱する非集中の精神に資することになりますし、<code>matrix.org</code>はときどき過負荷の状態に陥ります（最近では改善してきていますが）。またCloudflareを利用しているためセキュリティ上の懸念もあります。
</div>

### アカウントを登録する

<div class="flash">
  このパートは、ホームサーバが独自の認証ツールを利用しているケースを想定していません。そのようなケースでは各ホームサーバの解説をチェックしてください。
</div>

話を簡単にするため、このガイドではPC上のWebブラウザで登録を行なう前提としています。ただし多くのサーバではPCやモバイルのネイティブアプリからも登録することができます。いずれにせよ一度アカウントを登録すれば、そのアカウントはどこでも使うことができます。

1. このWebサイトのホームサーバ一覧には「In-house Element」のリンクがあるものがあります。あなたが登録しようとしているホームサーバにリンクがあれば、そこから登録してください。そうでなければ[Elementの公式Webクライアント](https://app.element.io)を利用してください。
2. 「アカウントを登録」をクリックしてください。
3. 登録ダイアログで、あなたが意図したホームサーバに登録しようとしているかを確認してください。必要であれば「編集」をクリックして適切なドメインを入力してください（あなたのホームサーバの説明か、[ホームサーバ一覧](../servers)の「Registration method」の項目を確認してください）。確認したら**ドメインをメモしておいてください**。ログインするときに必要になります[^7]。
4. 必要な情報を入力してください。
5. Eメールアドレスの入力を求められなければ、これで終わりです。そうでなければ、[ログイン](#log-into-an-existing-account)の前にアドレスの確認が必要になります。

すべてのユーザはそれぞれ固有のMXIDを持ちます。あなたのMXIDはユーザ名とサーバ名（必ずしもドメイン名とは一致しません）を組み合わせたものです。たとえば`@austin:tchncs.de`が筆者のMXIDですが、`austin`がユーザ名で`tchncs.de`がサーバ名です。別のユーザ名やホームサーバを使うには新しいアカウントを登録する必要があるので、*MXIDを後から変更することはできません*（[データの移行](https://ems.element.io/tools/matrix-migration)はできるかもしれません）。さらに、あなたがアカウントを無効化した場合、他の誰もそのMXIDを再利用することはできません。ただし、表示名やアバターの変更はいつでも行なうことができます。

[キーバックアップの設定](#set-up-key-backup)を忘れないでください。

### すでにあるアカウントにログインする

ほとんどのアプリで、
For most apps:

1. ログインダイアログを開いてください。
2. あなたが正しいサーバにログインしようとしていることを確認してください。大抵はダイアログの上のほうに表示されています。必要であれば「編集」をクリックして適切なドメインを入力してください（登録方法のステップ3と同じです）。
3. 詳しいログイン情報を入力してください。

### キーバックアップを設定する

When you log into a new device, you will be prompted to verify it using your existing device (by scanning a QR code or by comparing emojis). Your new device will then retrieve the room keys from your existing device, thereby enabling it to read your encrypted messages. This prevents anyone else - including your homeserver operator - to read encrypted content[^1].

However, a Security Key is required to access encrypted messages if:

* You have logged out of *all* your sessions prior to this login, or
* You are unable to verify interactively from another session.

You can set up a Security Key with the following steps:

1. On your first login, a bubble on the top-left will ask you to "set up secure backup". Click "Continue". If that is not the case, click your avatar, then "Settings" -> "Security & Privacy" -> "Secure Backup" -> click "Set up".
2. "Generate a Security Key" is enough.
3. Save the generated security key in a safe place (like in a password manager).

<div class="flash flash-warn">
  It is <b>strongly recommended</b> to do this step to prevent accidentally losing all of your encrypted messages.
</div>

## Get Familiar

### What app should I use?

There exists [many different apps](https://matrix.org/clients/) that can access Matrix. Because Matrix is an open protocol, you can even implement Matrix in your own app, if you got the skills. But for most people, here are some recommendations:

#### Browser

* [Element](https://app.element.io): The flagship app.
  * [Element development version](https://develop.element.io): Element with lab features enabled, but potentially unstable.
  * [SchildiChat](https://app.schildi.chat/): Element with lab features enabled, plus an optional speech bubble layout.
* [Cinny](https://cinny.in/): Matrix in Slack style.
* [Hydrogen](https://hydrogen.element.io/): Fast and adaptable to mobile browsers, at the cost of missing some optional features.

#### PC and Mobile

* [Element](https://element.io): The flagship app.
  * [SchildiChat](https://schildi.chat/): Element with lab features enabled, plus an optional speech bubble layout. Recommended to be used on PC for the full feature set.
* [FluffyChat](https://fluffychat.im/): "Cute" Matrix. Recommended to be used on mobile for performance.

For those living on the edge: [Commune](https://commune.chat/), [Nheko](https://github.com/Nheko-Reborn/nheko), [Spectral](https://spectral.im), and [Syphon](https://syphon.org/).

<div class="flash">
  For PC users, if you want a better experience when using Element or SchildiChat, place <a href="../assets/config.json">this config file</a> in your <a href="https://github.com/vector-im/element-desktop#user-specified-configjson">configuration folder</a>, where <code>$NAME</code> is either "Element" or "SchildiChat". The config file enables the "Labs" tab in settings, enables custom themes, preloads <a href="https://github.com/aaronraimist/element-themes">a few custom themes</a>, uses <a href="https://dimension.t2bot.io/">Dimension</a> instead of Scalar for integration manager, and preloads a few homeservers for room directory searches.
</div>

### What rooms can I join?

Each Matrix homeserver has a public room directory, which is accessible to the users of that homeserver or, if enabled, users of other homeservers as well.

* On PC, for Element and SchildiChat, click the "Explore Rooms" button below your username on the top-left.
* For FluffyChat, and for Element and SchildiChat on phone, click the search button.

In any case mentioned above, you can enter the room address to directly join a room, or you can enter keywords to search for rooms[^8]. However, the directory may be unintuitive to use as it orders rooms by member count[^9]. The author of this guide recommends joining [this Space](https://matrix.to/#/#offtopic-space:envs.net) (`#offtopic-space:envs.net`), which contains a list of active off-topic or no-topic discussion rooms.

#### Hold on, what's a Space?

Discord users may be familiar with this format, but Spaces are not exactly the same as a Discord "server." A Space[^10] is a list that can include other rooms and Spaces. It can be used to organize your own rooms, or for a community to organize all its rooms. Joining a Space does not imply joining all of its rooms (however, rooms can choose to require users to join a Space first), nor does leaving a Space imply leaving all of its rooms (by default).

On Element and SchildiChat, Spaces show up on the left of your room list. Selecting one will filter your room list to DMs with members of the Space and joined rooms within the Space. To see rooms that you have not yet joined, click the Explore button (see above).

## Go Deeper

<div class="flash flash-warn">
  The names of your sessions are public, which enable others to know what OS you're using (it used to be accurate to devices but that is no longer the case). You can rename them, however (as long as you know which is which):
  <ul>
    <li>In Element/SchildiChat, go to user settings, then "Security & Privacy." Rename the sessions as needed.</li>
    <li>In FluffyChat, go to settings, then "devices." Click the sessions to rename them.</li>
  </ul>
</div>

If you're using Element or SchildiChat, then keep the [Element User Guide](https://element.io/user-guide) handy for a quick reference to the interface!

* [More Features of Matrix](./features): An introduction to more of Matrix's features!
* [Public homeserver list](../servers)
* [Questions & Answers](./qna)

## Footnotes

[^1]: Only text contents and file attachments of messages are encrypted, using the Signal protocol. Currently, Matrix does not prevent metadata leakage, mainly due to its federated nature. This will change, however, when Matrix starts rolling out [Pinecone](https://archive.fosdem.org/2021/schedule/event/matrix_pinecones/), allowing p2p connections. Currently, it *can* be mitigated if all participants of an E2EE conversation are running their own homeserver (so to eliminate third parties).

[^2]: Exception: Some bots do not support end-to-end encrypted messaging. Furthermore, when creating an empty private room, you will be prompted (but not by default) to enable encryption.

[^3]: Element allows you to opt into (not enabled by default as of late 2021) using an "identity server" - think of it as a big online address book. This allows users to share their email addresses and username, which can be looked up manually by other users. However, here "address book" means that Matrix will not store the one locally on your phone; homeservers *can* see who you are talking to, as such information are not encrypted. There is [a proposal](https://github.com/matrix-org/matrix-doc/pull/3414) to address this. See also footnote 1.

[^4]: Note that public rooms may block certain servers - just like banning individual users - due to prevalence of unacceptable content (spam, hate speech, etc.). If you're not running your own homeserver, don't join homeservers that are known to harbour such content. This does not apply to homeservers listed on [our public list](../servers) as they are vetted against any presence of bad reputation. In any case, behave yourselves, remember the human.

[^5]: This includes all clients and servers that an average user uses.

[^6]: [Synapse](https://github.com/matrix-org/synapse/) is the only stable homeserver implementation as of now. If you are living on the edge, you can try out [Dendrite](https://github.com/matrix-org/dendrite/) and [Conduit](https://conduit.rs/), both of which aim to support p2p eventually (see footnote 1).

[^7]: In most cases, it is equivalent to the server part of your MXID. The exceptions are where homeservers did not set up `.well-known` autodiscovery properly...

[^8]: Title and description.

[^9]: Which is not a reasonable gauge of activity. First, accounts can be inactive. Second, if a room uses [bridges](./features/#all-about-bridges), then these accounts are counted as well, even if their activity is mostly not from Matrix (you can still interact with them, however).

[^10]: Which, to be exact, is a special type of rooms. Other than that you can list rooms (and Spaces) instead of sending messages, there are no differences between a Space and a room.
