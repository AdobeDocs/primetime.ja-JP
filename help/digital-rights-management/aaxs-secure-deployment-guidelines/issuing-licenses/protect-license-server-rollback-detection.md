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


# ロールバックの検出{#rollback-detection}

Adobeアクセスの実装で、クライアントが状態の維持を必要とするビジネスルール（再生時間間隔など）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFでリストを許可することを推奨します。

rollbackカウンタは、クライアントからの要求の大部分で、サーバに送信されます。 Adobeアクセスの実装にロールバックカウンタが必要ない場合は、無視できます。 それ以外の場合は、`MachineToken.getMachineId().getUniqueId()`を使用して取得したランダムマシンIDと現在のカウンタ値をAdobeに格納することを推奨します。 ロールバックカウンターの増分と追跡について詳しくは、『*AdobeアクセスAPIリファレンス*』の「ClientState」と『*コンテンツ保護用のAdobeアクセスSDKの使用*』の「*ロールバック検出*」を参照してください。
