---
description: 広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。
title: 広告挿入メタデータ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# 概要{#ad-insertion-metadata}

広告リゾルバーが機能するようにするには、Adobe Primetimead decisioningなどの広告プロバイダーがプロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioningライブラリが含まれています。 Primetime ad decisioningサーバーから広告をコンテンツに含めるには、アプリケーションが以下の必要な`AuditudeSettings`情報を提供する必要があります。

* `mediaID`は、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetimeのad decisioningサーバーに送信する際に`mediaID`を割り当てます。 このIDは、Primetime ad decisioningがサーバーからビデオに関連する広告情報を取得するために使用します。

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