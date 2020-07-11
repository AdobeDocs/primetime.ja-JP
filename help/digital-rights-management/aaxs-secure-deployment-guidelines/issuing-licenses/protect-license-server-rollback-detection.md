---
seo-title: ロールバックの検出
title: ロールバックの検出
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# ロールバックの検出 {#rollback-detection}

Adobe Accessの実装で、クライアントの状態の維持を必要とするビジネスルール（再生時間間隔など）を使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFで許可リストを使用することを強くお勧めします。

rollbackカウンタは、クライアントからの要求の大部分で、サーバに送信されます。 Adobe Accessの実装にロールバックカウンターが必要ない場合は、このカウンターを無視できます。 それ以外の場合は、を使用して取得したランダムマシンIDと現在のカウンタ値をデータベースに格納す `MachineToken.getMachineId().getUniqueId()`ることをお勧めします。 ロールバックカウンターの増分と追跡について詳しくは、『Adobe Access APIリファレンスのClientState *』および『* Adobe Access SDKを *使用したコンテンツの保護* 』の *Rollback detection*&#x200B;を参照してください。
