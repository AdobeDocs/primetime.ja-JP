---
seo-title: クライアントのアップグレード
title: クライアントのアップグレード
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d

---


# クライアントのアップグレード{#upgrading-clients}

FMRMS 1.xクライアントがAdobe Accessサーバーに接続する場合は、クライアントにアップグレードを求めるプロンプトを表示する必要があります。

* リクエストハンドラークラスはで `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`す。
* 要求URLは「*Base URL from 1.x content*」 + 「/edcws/services/urn:EDCLicenseService」です。

   他のAdobe Accessリクエストハンドラーとは異なり、このハンドラーはリクエスト情報へのアクセスを提供せず、応答データの設定を必須とします。 のインスタンスを作 `FMRMSv1RequestHandler`成し、 `close()`