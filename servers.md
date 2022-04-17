---
title: 公開されているMatrixホームサーバの一覧
ntitle: 公開ホームサーバ一覧
layout: page
nav: true
permalink: servers/
description: さまざまなホームサーバに参加することでMatrixの分散化をサポートしましょう。
---

<script>
document.addEventListener('DOMContentLoaded', (event) => {
  Array.from(document.getElementsByTagName("tr")).forEach(r => {
    let c = r.children;
    let i = 2;
    while(i < 4) {
      switch (c[i].textContent) {
        case "No":
          c[i].classList.add("red");
          break;
        case "Yes":
        case "CoC and ToS":
          c[i].classList.add("green");
          break;
        default:
          c[i].classList.add("orange");
      }
      i++;
    }
    i = r.children.length - 1;
    if (c[i].textContent == "Error!!")
      c[i].classList.add("red");
    else if (c[i].textContent.indexOf("Dendrite") == -1)
      c[i].classList.add((parseFloat(c[i].textContent.substring(2)) >= 47.1 && c[i].textContent != "1.49.0") ? "green" : "orange");
  })
})
</script>

## 公開されているMatrixホームサーバの一覧 {#list-of-public-matrix-homeservers}

これは公開されているMatrixホームサーバの一覧で、このガイドの筆者によってまとめられています。この一覧に関するサポートは[`#public_servers:tchncs.de`](https://matrix.to/#/#public_servers:tchncs.de)で提供されます。

* あなたのアカウントを継続して利用できるよう、あなたが信頼でき、[連携設定が適切](https://federationtester.matrix.org/)で、より新しいバージョンの、あなたの用途に適した、長期の運用が想定されたホームサーバを選ぶようにしてください。
* どのホームサーバも、ユーザ（つまり、あなた）のアカウントの暗号化されていない情報すべてにアクセスできることに注意してください。
* **これは大切なことです**が、公開された対話へのすべての参加者は互いを尊重できる環境を育むべきですし、ホームサーバの運営者は妨害行為などに適切に対処をすべきです。このため、素行の悪い参加者がいるとされるホームサーバはこの一覧から除外されています。[規範](#criteria)を参照してください。
* ホームサーバを運営する皆さんへ。[MSC1929](https://github.com/matrix-org/matrix-doc/blob/hs/proposal-admin-contact-1/proposals/1929-admin-contact.md)に対応してください。
* この一覧は[JSONフォーマット](../servers.json)でも提供されています。適切にクレジット表示さえしていただければ、クライアントへの組み込みも歓迎します。

**免責事項：**

* この一覧に掲載されているという事実をもって、各ホームサーバに対する何らかの見解（提携、支持など）や有用性に関する何らかの保証を、暗に表明するものでは**ありません**。
* この一覧は「現状のまま（as-is）」で提供されます。あるホームサーバにおけるあなたのアカウントに関する問題は、あなたと運営者の間で解決されるべきです。

**日本語版訳註：**

* 原著者の意向により、一覧の内容は原文ママです。
    * 「Open registration」：登録に特に条件がないサーバの一覧
    * 「Conditional registration」：登録に条件（独自の規定による制約、運営者による個別承認や課金の必要性）があるサーバの一覧
* オリジナル（英語版）の一覧は自動処理によって定期的に更新されていますが、日本語版へのマージは（今のところ）手動のためタイムラグが避けられません。厳密に最新の一覧が必要な場合は[英語版](https://joinmatrix.org/servers/)を参照してください。

一覧の各項目についての説明は[凡例](#legends)を参照してください。

{% capture my_include %}{% include matrix_prod.md %}{% endcapture %}
{{ my_include | markdownify }}

## なぜ？ {#why}

独自のホームサーバを運営するのが理想ではありますが、すべての人がその手段を持っているわけではありません… いずれにせよ、`matrix.org`以外のホームサーバを利用すべき理由があります。

1. `matrix.org`はしばしば過負荷のため不安定になります。
2. 特定のホームサーバにユーザが集中すると、Matrixが理想とする非集権化から遠のいてしまいます。

もしかすると、あなたのMXIDで特定のコミュニティへの所属を表明したいこともあるでしょう。

## 規範 {#criteria}

この一覧は以下の規範に則ってメンテナンスされています。

* ホームサーバが広く一般からアカウント登録を受け付けていること。
    * 掲載の判断は原則として、ホームサーバーに関する情報の筆者による解釈、もしくはホームサーバーの運営者の明確な同意のいずれかに基づきます。
    * 登録に承認が必要なホームサーバについては、そのプロセスが広く一般に公開されている必要があります。
    * ホームサーバが新規登録を一時停止することがありますが、その場合は一覧からも一時的に除外されます。
* ホームサーバ名がセカンドレベルドメインであること（つまり`example.com`は掲載対象ですが、`matrix.example.com`は対象外です）。[Synapseのドキュメント](https://matrix-org.github.io/synapse/latest/delegate.html)を参照してください。
* ホームサーバが無料のTLD、特にFreenomから提供されているTLDを使用していないこと（第三者によって不正に奪取されるリスクがあるため）。
* ホームサーバが運営されているドメイン上に、意味あるWebページ（Elementを含む）が少なくとも一つは存在すること。
* ホームサーバが`matrix.org`でなく、またElement Matrix Services（以前はModularという名前でした）を利用していないこと。
* ホームサーバが以下のMjolnirバン（`m.room.rule.server`）の対象でないこと。
  * `#matrix-org-coc-bl:matrix.org`: [matrix.org行動規範](https://matrix.org/legal/code-of-conduct/)に基づくバンリスト。人気のある公開ルームの多くで利用されています。
  * `#matrix-org-hs-tos-bl:matrix.org`: [matrix.orgホームサーバ利用規約](https://matrix.org/legal/terms-and-conditions/)に基づくバンリスト。

一部のホームサーバはそのコンテンツを理由として一覧から除外されています。上記以外の評価の高いバンリストに掲載されることも、この一覧からの除外理由になることがあります。

## 凡例 {#legends}

左から順に記載します。

* **Homeserver name**（ホームサーバ名）：この名前があなたのユーザ名の後ろにつきます。たとえば、私のIDは`@austin:tchncs.de`ですが、このうち`austin`がユーザ名で`tchncs.de`がホームサーバの表示名です。技術的な解説は[ここ](https://spec.matrix.org/v1.1/server-server-api/#resolving-server-names)を参照してください。
* **Jurisdiction (and Server location)**（司法権とサーバ所在地）：ホームサーバが属する司法権の管轄範囲です。司法権の範囲と異なる場合は、サーバの所在地を括弧書きで追記します。一般的に、ドイツに所在するホームサーバでは[法的もしくは社会的文脈で](https://en.wikipedia.org/wiki/Censorship_in_Germany#Re-unified_Germany_(1990%E2%80%93present))より積極的にモデレーションが行なわれる傾向にあります。
* **Rules?**（規約が存在するか？）：すべてのユーザ向けに文書化された利用規約が存在するか否かです。利用規約がユーザのすべての活動（特定のルーム内だけでない）に適用され、Webページとして公開されている（`/_matrix/consent`を含みますがこれに限りません）場合に限り、この項目の検討対象になります。unclear（不明確）やsort of（ある種の；黄色で表示）は、利用規約の適用範囲や内容が不明確なことを示します。
* **Privacy Policy?**（プライバシーポリシーが存在するか？）：すべてのユーザ向けに文書化されたプライバシーポリシーが存在するか否かです。一般に、[「あなたのデータがどう扱われるか」に関する告知](https://matrix-client.matrix.org/_matrix/consent?v=1.0)のほとんどが、ネットワーク全体に適用されます。プライバシーポリシーがMatrixホームサーバに適用されることが明確であり、Webページとして公開されていて（`/_matrix/consent`を含みますがこれに限りません）、内容が前述の告知のコピーでない場合に限り、この項目の検討対象になります。unclear（不明確）やsort of（ある種の；黄色で表示）は、プライバシーポリシーの適用範囲や内容が不明確なことを示します。
* **Note**（備考）：その他の特記事項です。ホームサーバのドメイン名からその主題や方針が読み取れることがありますので、その場合はこの項目には記載しません。懸念事項は*斜体*で表示されます。
    * Age restriction（年齢制限）：Matrixは16歳以上向けですが、より高い年齢向けのホームサーバであることを示します。
    * Accessory（付属的）：運営者（たいていは何らかのプロジェクト）に関連するルームに特化したホームサーバであることを示します。そのため公開ルームディレクトリに掲載する際は十分に配慮してください。しかし、アカウントは外部のルームにアクセスするのに使うこともできます。
    * Residential（家庭用）：ホームサーバが一般家庭向けのインターネット接続で運用されている可能性があることを示します（訳註：いわゆる「自宅サーバ」）。
  * ...-oriented（〜向け）：ホームサーバが特定の目的で運営されていることを示します。
  * ...-inclined（〜傾向）：ホームサーバ自身は特定の目的で運営されているわけではないにもかかわらず、特定の目的で利用される傾向にあることを示します。
* **Registration method**（登録方法）：アカウント登録の手続きに関する情報です。[Elementの公式Webクライアント](https://app.element.io)で（必ずしも完全ではありませんが）テストを行なっています。またほとんどの場合、他のクライアントでも登録が行なえるはずです。
    * In-house Element（インハウスElement）：リンク先の、ホームサーバ自身がホストするElementクライアントを使って[登録](../guide/#register-an-account)ができます。これは大抵の場合、reCaptchaのドメイン制限に対応するためです。
    * Form（フォーム）：リンク先のフォームから登録ができます。
    * See info page（情報ページを参照）：サーバ名の欄からリンクされたページを参照してください。
    * ドメイン名：このホームサーバにアカウントを[登録](../guide/#register-an-account)する際、「アカウントを作成」と「編集」をクリックした後、この欄に記載されたドメイン名（`https://`は含まない）を入力する必要があります。この不一致は大抵の場合、`.well-known`の設定ミスに起因します。
    * SSO（シングルサインオン）：ホームサーバはユーザ認証に[シングルサインオン](https://en.wikipedia.org/wiki/Single_sign-on)を要求します。Matrixアカウントの前に、リンク先からアカウントの作成を行なう必要があります。大抵の場合、そのアカウントはホームサーバの運営者が提供する他のサービスへのアクセスにも利用できます。
* **Version**（バージョン）：ホームサーバのソフトウェアバージョンです。[GitHub Actionで6時間ごとに自動更新されます](https://github.com/austinhuang0131/joinmatrix/blob/main/.github/workflows/matrix_ver.yml#L4)。
    * 他に明記されていない場合、ホームサーバはSynapseで稼働しています。Synapseはセキュリティ上の問題のため`1.47.1`以降（緑色で表示）の利用が[推奨されています](https://matrix.org/blog/2021/11/23/synapse-1-47-1-released)。非推奨のバージョン、つまり`1.47.1`以前と`1.49.0`（[リグレッション](https://github.com/matrix-org/synapse/pull/11583)のため）は黄色で表示されます。
    * Dendriteで稼働しているホームサーバは無色で表示されます。
    * Error!!（赤色で）：チェックの際にホームサーバに接続ができなかったことを示します。これは大抵一時的なものですが、頻繁に発生する場合は一覧からの除外理由となります。

## 他のMatrixホームサーバ一覧 {#other-matrix-homeserver-lists}

* [asra.gr's list](https://wiki.asra.gr/en:public_servers)：一般からの登録を（一部は意図的ではないにしろ）受け付けているホームサーバのデータセット
* [CHATONS list](https://www.chatons.org/search/by-service?service_type_target_id=All&field_alternatives_aux_services_target_id=All&field_software_target_id=274&field_is_shared_value=All&title=): 一定の倫理基準を満たしたフランスのホームサーバの一覧。一部はメンバーシップが必要な可能性があります
* [German homeservers list](https://fediverse.blog/~/FossMessenger/matrix-server): ドイツに所在するホームサーバの一覧

この一覧は、以前は[AustinHuang.me](https://austinhuang.me/matrix-homeservers.html)で公開されていました。
