---
title: Get Server Version リクエストの処理
description: Get Server Version リクエストの処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Get Server Version リクエストの処理 {#handle-get-server-version-requests}

Adobe Primetime DRM クライアント 3.0 以降は、サーバーの機能を判断するための Get Server Version リクエストを送信します。 Primetime DRM SDK 3.0 以降を使用するすべてのサーバーは、Get Server Version リクエストのサポートを実装する必要があります。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* リクエスト URL は、「メタデータのライセンスサーバー URL」+「」である必要があります [!DNL /flashaccess/getServerVersion/v3]&quot;

Primetime DRM SDK 4.0 以降の場合、 Get Server Version 要求への応答は、サーバーが Primetime DRM プロトコルのバージョン 3 および 4 をサポートしていることをクライアントに示します。
