---
seo-title: クライアントのアップグレード
title: クライアントのアップグレード
uuid: 9c9bc7da-2a97-4659-945a-554d778d30a3
translation-type: tm+mt
source-git-commit: 5cf90a75d8805fb64d7d145722ad10a1ce77a14d
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# クライアントのアップグレード{#upgrading-clients}

FMRMS 1.xクライアントがAdobeアクセスサーバーと通信する場合、サーバーはクライアントにアップグレードを促すプロンプトを表示する必要があります。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`です。
* 要求URLは、&quot;*1.x content*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;のベースURLです

   他のAdobeアクセス要求ハンドラとは異なり、このハンドラは要求情報へのアクセスを提供せず、応答データの設定を必要とします。 `FMRMSv1RequestHandler`のインスタンスを作成し、`close()`を呼び出します