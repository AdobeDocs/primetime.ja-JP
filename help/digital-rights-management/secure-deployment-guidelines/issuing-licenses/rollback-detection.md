---
description: Adobe PrimetimeDRMの実装で、クライアントの状態の維持を必要とするビジネスルール（例えば、再生ウィンドウの間隔）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFで許可リストを使用することを推奨します。
seo-description: Adobe PrimetimeDRMの実装で、クライアントの状態の維持を必要とするビジネスルール（例えば、再生ウィンドウの間隔）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFで許可リストを使用することを推奨します。
seo-title: ロールバックの検出
title: ロールバックの検出
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# ロールバックの検出{#rollback-detection}

Adobe PrimetimeDRMの実装で、クライアントの状態の維持を必要とするビジネスルール（例えば、再生ウィンドウの間隔）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFで許可リストを使用することを推奨します。

rollbackカウンタは、クライアントからの要求の大部分で、サーバに送信されます。 Primetime DRMの実装にロールバックカウンターが必要ない場合は、無視できます。 それ以外の場合は、Adobeは、[MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())を使用して取得したランダムなマシンIDと、現在のカウンタ値をデータベースに格納することを推奨します。

ロールバックカウンタを増分および追跡する方法の詳細については、[ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html)とRollback detectionを参照してください。