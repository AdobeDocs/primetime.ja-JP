---
description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: ee4dd8b8-4c41-4f01-be50-60f4c7dc962d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# 概要{#ad-insertion-metadata-overview}

広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioninglibraryが含まれています。 Primetime ad decisioningserverから広告をコンテンツに含めるには、アプリケーションが以下の必要な`AuditudeSettings`情報を提供する必要があります。

* `mediaID`は、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetimead decisioningサーバーに送信する際にmediaIDを割り当てます。 このIDは、Primetime ad decisioningがサーバーからビデオに関連する広告情報を取得するために使用します。

* （オプション）`defaultMediaId`。以下の条件が満たされた場合に提供される広告を指定します。

   * 広告サーバーへのリクエストが無効か、コンテンツが正しく設定されていません。
   * Primetime ad decisioningで、データのプロパゲートに遅延が発生している。
   * Primetime ad decisioningのバックエンドプロセスの1つが正常に機能しないか、使用できません。

   >[!TIP]
   >
   >Adobeは`defaultMediaId`の使用を推奨します。

* `zoneID`は、Adobeによって割り当てられ、会社またはWebサイトを特定します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   広告プロバイダーのニーズおよびニーズに応じて、これらのパラメーターを含めることができます。