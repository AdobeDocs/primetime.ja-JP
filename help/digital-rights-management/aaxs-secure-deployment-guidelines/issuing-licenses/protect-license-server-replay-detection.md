---
seo-title: 再生保護
title: 再生保護
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# リプレイ保護{#replay-protection}

リプレイ保護は、攻撃者がライセンス要求メッセージを再生したり、潜在的にDoS(DoS)攻撃をクライアントに対して引き起こすのを防ぎます（A *Do-of-Service*&#x200B;攻撃は、攻撃者がサービスの正当なユーザーに対して使用を防ぐ試みです）。 例えば、ロールバックカウンターを使用した再生攻撃を使用して、DRMクライアントが状態をロールバックしていると判断して、License Serverを「騙し取り」、アカウントを停止させることができます。

リプレイ保護の詳細については、`AbstractRequestMessage.getMessageId()`『AdobeアクセスAPIリファレンス&#x200B;*』を参照してください。*
