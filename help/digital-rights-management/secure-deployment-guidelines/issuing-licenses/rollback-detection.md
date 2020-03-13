---
description: Adobe Primetime DRMの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFホワイトリストを使用することをお勧めします。
seo-description: Adobe Primetime DRMの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFホワイトリストを使用することをお勧めします。
seo-title: ロールバックの検出
title: ロールバックの検出
uuid: f161ed41-488a-478a-b6a8-468cf6d11e89
translation-type: tm+mt
source-git-commit: 3fdef12b717bb6f70ca27d9278de61d709f8349c

---


# ロールバックの検出 {#rollback-detection}

Adobe Primetime DRMの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFホワイトリストを使用することをお勧めします。

rollbackカウンタは、クライアントからのほとんどの要求でサーバに送信されます。 Primetime DRMの実装にロールバックカウンターが不要な場合は、無視できます。 それ以外の場合は、MachineToken.getUniqueId()を使用して取得したランダムなマシンIDと、現在のカウンター値をデータベースに格納することをアドビは [](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())、サーバーに推奨します。

ロールバックカウンターを増分および追跡する方法の詳細については、 [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) and Rollback detectionを参照してください。