---
title: リプレイの保護
description: リプレイの保護
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# リプレイの保護{#replay-protection}

再生保護は、攻撃者がライセンスリクエストメッセージを再生するのを防ぎ、潜在的に DoS(DoS) 攻撃をクライアント (A) に対して行うのを防ぎます。 *サービス拒否* 攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用するのを防ぐための試みです。 例えば、ロールバックカウンターを使用した再生攻撃を使用して、DRM クライアントが状態をロールバックし、アカウントの停止を引き起こしているとライセンスサーバーを「欺く」ことができます。

再生保護の詳細については、 `AbstractRequestMessage.getMessageId()` の *Adobeアクセス API リファレンス*.
