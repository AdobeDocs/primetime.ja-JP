---
seo-title: Get Server Version要求の処理
title: Get Server Version要求の処理
uuid: 6e287f58-2ad2-428a-a76a-6847d06b0fd8
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Get Server Version要求を処理{#handle-get-server-version-requests}

Adobe PrimetimeDRMクライアント3.0以降は、サーバーの機能を判断するための「Get Server Version」要求を送信します。 Primetime DRM SDK 3.0以降を使用しているすべてのサーバーは、Get Server Version要求のサポートを実装する必要があります。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`です
* 要求URLは、「メタデータのライセンスサーバーURL」 + 「 [!DNL /flashaccess/getServerVersion/v3]」にする必要があります。

Primetime DRM SDK 4.0以降の場合、Get Server Versionリクエストに対する応答は、サーバーがPrimetime DRMプロトコルのバージョン3と4をサポートしていることをクライアントに示します。
