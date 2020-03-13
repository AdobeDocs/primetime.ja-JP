---
seo-title: 再生保護
title: 再生保護
uuid: 5e6488e6-0834-4dcf-bc26-55019f5db320
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 再生保護{#replay-protection}

再生保護は、攻撃者がライセンス要求メッセージを再生し、潜在的にDoS(DoS)攻撃をクライアントに対して引き起こすのを防ぎます(攻撃者による *DoS* (DoS)攻撃は、サービスの正当なユーザーがそのサービスを使用するのを防ぐ試みです)。 例えば、ロールバックカウンターを使用した再生攻撃を使用して、DRMクライアントが状態をロールバックし、アカウントの停止を引き起こしていると考えるように、ライセンスサーバーを「騙し」ます。

再生保護について詳しくは、『 `AbstractRequestMessage.getMessageId()` Adobe Access API Reference』を参照してください **。
