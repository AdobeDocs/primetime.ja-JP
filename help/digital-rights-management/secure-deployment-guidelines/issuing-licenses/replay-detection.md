---
description: リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。
title: 再生保護
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---


# リプレイ保護{#replay-protection}

リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。

DoS攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用できないようにする試みです。 例えば、ロールバックカウンターを使用するリプレイ攻撃を使用して、DRMクライアントが状態をロールバックしたと判断して、License Serverを「騙し取り」、アカウントを停止させることができます。

リプレイ保護の詳細については、[ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())を参照してください。
