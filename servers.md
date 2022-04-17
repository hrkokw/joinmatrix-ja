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

## 公開されているMatrixホームサーバの一覧

これは公開されているMatrixホームサーバの一覧で、このガイドの筆者によってまとめられています。この一覧に関するサポートは[`#public_servers:tchncs.de`](https://matrix.to/#/#public_servers:tchncs.de)で提供されます。

* あなたのアカウントを継続して利用できるよう、あなたが信頼でき、[連携設定が適切](https://federationtester.matrix.org/)で、より新しいバージョンの、あなたの用途に適した、長期の運用が想定されたホームサーバを選ぶようにしてください。
* どのホームサーバも、ユーザ（つまり、あなた）のアカウントの暗号化されていない情報すべてにアクセスできることに注意してください。
* **これは大切なことです**が、公開された対話へのすべての参加者は互いを尊重できる環境を育むべきですし、ホームサーバの運営者は妨害行為などに適切に対処をすべきです。このため、素行の悪い参加者がいるとされるホームサーバはこの一覧から除外されています。[規範](#criteria)を参照してください。
* ホームサーバを運営する皆さんへ。[MSC1929](https://github.com/matrix-org/matrix-doc/blob/hs/proposal-admin-contact-1/proposals/1929-admin-contact.md)に対応すべきです。
* この一覧は[JSONフォーマット](../servers.json)でも提供されています。適切にクレジット表示さえしていただければ、クライアントへの組み込みも歓迎します。

**免責事項：**

* この一覧に含まれているという事実をもって、各ホームサーバに対する何らかの見解（提携、支持など）や有用性に関する何らかの保証を、暗に表明するものでは**ありません**。
* この一覧は「現状のまま」で提供されます。あるホームサーバにおけるあなたのアカウントに関する問題は、あなたと運営者の間で解決されるべきです。

**日本語版訳註：**

* 原著者の意向により、一覧の内容は原文ママです。
* オリジナル（英語版）の一覧は自動処理によって定期的に更新されていますが、日本語版へのマージは（今のところ）手動のためタイムラグが避けられません。厳密に最新の一覧が必要な場合は[英語版](https://joinmatrix.org/servers/)を参照してください。

一覧の各項目についての説明は[凡例](#legends)を参照してください。

{% capture my_include %}{% include matrix_prod.md %}{% endcapture %}
{{ my_include | markdownify }}

## Why?

Ideally you would host your own homeserver, but not everyone has the means... Anyway, you should use a homeserver other than the default `matrix.org` because...

1. It is overloaded at times, and
2. If everyone continues to register on the same homeserver, then Matrix will become less decentralized as intended.

In some cases you might also want your MXID to show your affiliation with a specific community.

## Criteria

The absolute criteria are:

* The homeserver is intended for public registration.
  * Generally, inclusion is based on either my interpretation of information about the homeserver, or explicit consent from the homeserver operator(s).
  * Homeservers that grant accounts on approval must have such process accessible to the general public.
  * Homeservers may disable registrations temporarily, in which case the list will temporarily exclude them.
* The homeserver name must be a second-level domain (so `example.com` is acceptable, but `matrix.example.com` is not). See [Synapse documentation](https://matrix-org.github.io/synapse/latest/delegate.html).
* The homeserver does not operate through a free TLD, specifically those offered by Freenom (due to risks of takeover by fraudulent entities).
* The domain that the homeserver is on must have at least one meaningful web page (including Element).
* The homeserver is neither `matrix.org` nor operated by Element Matrix Services (previously known as Modular).
* The homeserver does not have an ongoing Mjolnir server ban (`m.room.rule.server`) on:
  * `#matrix-org-coc-bl:matrix.org`: [matrix.org Code of Conduct](https://matrix.org/legal/code-of-conduct/) ban list. It is used on many popular public rooms.
  * `#matrix-org-hs-tos-bl:matrix.org`: [matrix.org Homeserver Terms of Service](https://matrix.org/legal/terms-and-conditions/) ban list.

Some homeservers are excluded from this list on content grounds. Inclusion in other reputable ban lists may also be grounds for exclusion from this list.

## Legends

From left to right:

* **Homeserver name**: This is the part that follows your username. For example, my ID is `@austin:tchncs.de`, where `austin` is my username and `tchncs.de` is the display name of the homeserver. See [here](https://spec.matrix.org/v1.1/server-server-api/#resolving-server-names) for a technical explanation.
* **Jurisdiction (and Server location)**: The jurisdiction the homeserver is located within. The server location, if differs from the jurisdiction of the homeserver, is shown in the brackets. Note that generally, homeservers located in Germany are more actively moderated due to [legal and social contexts](https://en.wikipedia.org/wiki/Censorship_in_Germany#Re-unified_Germany_(1990%E2%80%93present)).
* **Rules?**: The existence of written rules/ToS for all users on the homeserver. Note that rules can only be considered if they apply to all activities (not just those in specific rooms) of a user, and if they are published in a webpage (including but not limited to `/_matrix/consent`). An "unclear" or "sort of" (colored yellow) means that the rules' scope or wording is unclear.
* **Privacy Policy?**: The existence of written privacy policy for all users on the homeserver. Generally, most parts of the ["Understand how your data is used" notice](https://matrix-client.matrix.org/_matrix/consent?v=1.0) apply network-wide. Note that a privacy policy can only be considered if it is explicitly applied to the Matrix homeserver, is published in a webpage (including but not limited to `/_matrix/consent`), and is not a copy of the aforementioned notice. An "unclear" or "sort of" (colored yellow) means the privacy policy's scope or wording is unclear.
* **Note**: Miscellaneous remarks. Note that a homeserver's theme/orientation can sometimes be seen from the domain itself, in which case it will not be noted down here. Anti-features are *italicized*.
  * Age restriction: Matrix is 16+. Homeservers that require users to be older are specified.
  * "Accessory": The homeserver is specifically intended for rooms related to the operator (usually a project), so please be considerate in listing rooms in the public room directory. However, the accounts can be used to access other federated rooms as well.
  * "Residential": The homeserver may be hosting on a residential internet connection.
  * "...-oriented": The homeserver is intended to serve the mentioned purpose.
  * "...-inclined": While the homeserver is not specifically intended to serve any purpose, it is nevertheless used for the mentioned purpose.
* **Registration method**: Exact registration procedure. Those are tested (but not necessarily thoroughly) on [the official Element web client](https://app.element.io) and, in most cases, should work for other clients as well.
  * "In-house Element": You may [register](../guide/#register-an-account) using the Element client hosted on the homeserver, which is linked. This is usually due to reCaptcha domain restriction.
  * "Form": You may register using the linked form.
  * "See info page": Refer to the page linked in the "server name" column.
  * A domain: After clicking "Create Account" and "Edit," enter the domain as specified in this column (without `https://`) to [create an account](../guide/#register-an-account) on this homeserver. This discrepancy is usually due to the misconfiguration of `.well-known`.
  * "SSO": The homeserver requires [single sign-on](https://en.wikipedia.org/wiki/Single_sign-on) for authentication. You must create an account through the link prior to creating an account on the Matrix homeserver itself. Usually, the account can be used to access other services offered by the homeserver operator.
* **Version**: The software version of the homeserver, [updated every 6 hours by a GitHub Action](https://github.com/austinhuang0131/joinmatrix/blob/main/.github/workflows/matrix_ver.yml#L4).
  * Unless indicated otherwise, the homeserver is running Synapse, where versions `1.47.1` and above (coloured green) is [recommended](https://matrix.org/blog/2021/11/23/synapse-1-47-1-released) to address a security issue. Homeservers running deprecated versions, namely those prior to `1.47.1`, as well as `1.49.0` (due to a [regression](https://github.com/matrix-org/synapse/pull/11583)), are coloured yellow.
  * Homeservers that use Dendrite are not coloured.
  * "Error!!" (coloured red): The homeserver cannot be reached at the time of checking. This is usually occasional, as frequent downtime are grounds for exclusion from this list.

## Other Matrix homeserver lists

* [asra.gr's list](https://wiki.asra.gr/en:public_servers): A raw dataset of homeservers that allows (but are not necessarily intended for) public registration.
* [CHATONS list](https://www.chatons.org/search/by-service?service_type_target_id=All&field_alternatives_aux_services_target_id=All&field_software_target_id=274&field_is_shared_value=All&title=): A list of homeservers hosted in France that adhere to certain ethical standards. Some may require membership.
* [German homeservers list](https://fediverse.blog/~/FossMessenger/matrix-server): A list of homeservers hosted in Germany.

This list was originally located at [AustinHuang.me](https://austinhuang.me/matrix-homeservers.html).
