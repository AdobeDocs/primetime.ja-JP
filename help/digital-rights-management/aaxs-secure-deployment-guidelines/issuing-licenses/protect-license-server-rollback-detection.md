---
title: ロールバックの検出
description: ロールバックの検出
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# ロールバックの検出{#rollback-detection}

Adobeアクセスの実装で、クライアントが状態の維持を必要とするビジネスルール（再生時間間隔など）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFでリストを許可することを推奨します。

rollbackカウンタは、クライアントからの要求の大部分で、サーバに送信されます。 Adobeアクセスの実装にロールバックカウンタが必要ない場合は、無視できます。 それ以外の場合は、`MachineToken.getMachineId().getUniqueId()`を使用して取得したランダムマシンIDと現在のカウンタ値をAdobeに格納することを推奨します。 ロールバックカウンターの増分と追跡について詳しくは、『*AdobeアクセスAPIリファレンス*』の「ClientState」と『*コンテンツ保護用のAdobeアクセスSDKの使用*』の「*ロールバック検出*」を参照してください。
