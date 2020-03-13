---
description: 再生保護を使用すると、攻撃者がライセンス要求メッセージを再生したり、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぐことができます。
seo-description: 再生保護を使用すると、攻撃者がライセンス要求メッセージを再生したり、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぐことができます。
seo-title: 再生保護
title: 再生保護
uuid: 93749dd3-a42c-4866-ac54-1b20d6683c42
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 再生保護{#replay-protection}

再生保護を使用すると、攻撃者がライセンス要求メッセージを再生したり、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぐことができます。

DoS攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用できないようにする試みです。 例えば、ロールバックカウンターを使用するリプレイ攻撃を使用して、DRMクライアントが状態をロールバックしたと判断し、アカウントが停止する原因となるように、ライセンスサーバーを「騙し」取ることができます。

再生保護について詳しくは、AbstractRequestMessage.getMessageId() [ を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())。
