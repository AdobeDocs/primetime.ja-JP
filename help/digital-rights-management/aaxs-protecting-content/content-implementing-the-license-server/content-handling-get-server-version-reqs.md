---
title: Get Server Version リクエストの処理
description: Get Server Version リクエストの処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Get Server Version リクエストの処理{#handling-get-server-version-requests}

Adobeアクセスクライアント 3.0 以降は、サーバーの機能を判断するために Get Server Version リクエストを送信します。 Adobeアクセス SDK 3.0 以降を使用するすべてのサーバーは、Get Server Version リクエストのサポートを実装する必要があります。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* リクエスト URL は、「メタデータのライセンスサーバー URL」+「/flashaccess/getServerVersion/v3」である必要があります。

Adobeアクセス SDK 4.0 以降では、 Get Server Version リクエストへの応答は、Adobeがサーバーアクセスプロトコルのバージョン 3 および 4 をサポートしていることをクライアントに示します。
