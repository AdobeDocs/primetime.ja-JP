---
description: リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。
seo-description: リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。
seo-title: 再生保護
title: 再生保護
uuid: 93749dd3-a42c-4866-ac54-1b20d6683c42
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---


# リプレイ保護{#replay-protection}

リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。

DoS攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用できないようにする試みです。 例えば、ロールバックカウンターを使用するリプレイ攻撃を使用して、DRMクライアントが状態をロールバックしたと判断して、License Serverを「騙し取り」、アカウントを停止させることができます。

リプレイ保護の詳細については、[ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())を参照してください。
