---
title: クライアントのアップグレード
description: クライアントのアップグレード
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# クライアントのアップグレード{#upgrading-clients}

FMRMS 1.x クライアントがAdobe・アクセス・サーバにアクセスする場合、サーバはクライアントにアップグレードを促すプロンプトを表示する必要があります。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* リクエスト URL は「*1.x コンテンツからのベース URL*&quot; + &quot;/edcws/services/urn:EDCLicenseService&quot;

  他のAdobeアクセス要求ハンドラーとは異なり、このハンドラーは要求情報にアクセスしたり、応答データを設定する必要はありません。 のインスタンスを作成します。 `FMRMSv1RequestHandler`を呼び出してから、を呼び出します。 `close()`
