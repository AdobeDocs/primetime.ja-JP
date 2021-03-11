---
title: クライアントのアップグレード
description: クライアントのアップグレード
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# クライアントのアップグレード{#upgrading-clients}

FMRMS 1.xクライアントがAdobeアクセスサーバーと通信する場合、サーバーはクライアントにアップグレードを促すプロンプトを表示する必要があります。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`です。
* 要求URLは、&quot;*1.x content*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;のベースURLです

   他のAdobeアクセス要求ハンドラとは異なり、このハンドラは要求情報へのアクセスを提供せず、応答データの設定を必要とします。 `FMRMSv1RequestHandler`のインスタンスを作成し、`close()`を呼び出します