---
description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 概要 {#ad-insertion-metadata}

広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

TVSDKには、Primetime ad decisioningライブラリが含まれています。 Primetime ad decisioningサーバーからの広告をコンテンツに含めるには、アプリケーションが次の必要な情報を提供する必要があ `AuditudeSettings` ります。

* `mediaID`に含まれている場合、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテ `mediaID` ンツおよび広告情報をAdobe Primetime Ad Decisioningサーバーに送信する際に、これを割り当てます。 このIDは、Primetime ad decisioningで、サーバーからビデオに関連する広告情報を取得するために使用されます。

* （オプション） `defaultMediaId`は、次の条件が満たされた場合に提供される広告を指定します。

   * 広告サーバーへの要求が無効か、コンテンツが正しく設定されていません。
   * Primetime ad decisioningで、データの伝播に遅延が発生している。
   * Primetime ad decisioningのバックエンドプロセスの1つが正常に機能していないか、使用できません。
   >[!TIP]
   >
   >アドビでは、を使用することをお勧めしま `defaultMediaId`す。

* アドビ `zoneID`が割り当てたユーザーは、会社またはWebサイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   これらのパラメーターは、ニーズおよび広告プロバイダーのニーズに応じて含めることができます。