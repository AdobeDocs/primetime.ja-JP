---
description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# 概要{#ad-insertion-metadata-overview}

広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。

ブラウザーTVSDKには、Adobe PrimetimeAd Decisioningライブラリが含まれています。 コンテンツにAdobe Primetimead decisioningサーバーからの広告を含めるには、アプリケーションが以下の必要なAudidetuceSettings情報を提供する必要があります。

* `mediaID`は、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetimead decisioningサーバーに送信する際にmediaIDを割り当てます。 このIDは、Adobe Primetimead decisioningがサーバーからビデオに関連する広告情報を取得するために使用します。

* （オプション）`defaultMediaId`。以下の条件が満たされた場合に提供される広告を指定します。

   * 広告サーバーへのリクエストが無効か、コンテンツが正しく設定されていません。
   * Adobe Primetimead decisioningでデータの伝播に遅延が発生している。
   * Adobe Primetimead decisioningのバックエンドプロセスの1つが正常に機能しないか、使用できません。

   >[!TIP]
   >
   >Adobeは`defaultMediaId`の使用を推奨します。

* `zoneID`は、Adobeによって割り当てられ、会社またはWebサイトを特定します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   広告プロバイダーのニーズおよびニーズに応じて、これらのパラメーターを含めることができます。