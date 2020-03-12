---
description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: 676e81b9-4c2b-487e-bc68-74879ca2966b
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 概要 {#ad-nsertion-metadata-overview}

広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioningライブラリが含まれています。 コンテンツにPrimetime ad decisioningサーバーからの広告を含めるには、アプリケーションが次の必要な情報を提供する必要があ `AuditudeSettings` ります。

* `mediaID`に含まれている場合、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetime Ad Decisioningサーバーに送信する際に、mediaIDを割り当てます。 このIDは、Primetime ad decisioningで、サーバーからビデオに関連する広告情報を取得するために使用されます。

* （オプション） `defaultMediaId`は、次の条件が満たされた場合に提供される広告を指定します。

   * 広告サーバーへの要求が無効か、コンテンツが正しく設定されていません。
   * Primetime広告の判定で、データの反映に遅延が発生している。
   * Primetime ad decisioningのバックエンドプロセスの1つが正常に機能していないか、使用できません。
   >[!TIP]
   >
   >アドビでは、を使用することをお勧めしま `defaultMediaId`す。

* アドビ `zoneID`が割り当てたユーザーは、会社またはWebサイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   これらのパラメーターは、ニーズおよび広告プロバイダーのニーズに応じて含めることができます。