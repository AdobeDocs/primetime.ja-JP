---
title: Get Server Version要求の処理
description: Get Server Version要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Get Server Version要求の処理{#handling-get-server-version-requests}

Adobeアクセスクライアント3.0以降は、サーバーの機能を判断するためにGet Server Version要求を送信します。 AdobeアクセスSDK 3.0以降を使用しているすべてのサーバーは、Get Server Version要求のサポートを実装する必要があります。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`です
* 要求URLは、「メタデータのライセンスサーバーURL」 + 「/flashaccess/getServerVersion/v3」である必要があります。

AdobeアクセスSDK 4.0以降では、Get Server Version要求に対する応答は、サーバーがAdobeアクセスプロトコルのバージョン3と4をサポートしていることをクライアントに示します。
