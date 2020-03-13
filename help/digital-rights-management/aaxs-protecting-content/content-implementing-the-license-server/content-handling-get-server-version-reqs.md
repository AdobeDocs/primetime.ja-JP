---
seo-title: Get Server Version要求の処理
title: Get Server Version要求の処理
uuid: a3084faa-cf3d-45cc-a244-298308c4cf15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Get Server Version要求の処理{#handling-get-server-version-requests}

Adobe Accessクライアント3.0以降は、サーバーの機能を判断するために、Get Server Versionリクエストを送信します。 Adobe Access SDK 3.0以降を使用するすべてのサーバーで、Get Server Versionリクエストのサポートを実装する必要があります。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* 要求URLは、「メタデータのライセンスサーバーURL」 + 「/flashaccess/getServerVersion/v3」である必要があります。

Adobe Access SDK 4.0以降の場合、Get Server Versionリクエストに対する応答は、サーバーがAdobe Accessプロトコルのバージョン3と4をサポートしていることをクライアントに示します。
