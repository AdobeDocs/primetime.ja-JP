---
title: Get Server Version要求の処理
description: Get Server Version要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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
