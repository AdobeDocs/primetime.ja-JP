---
description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-description: 広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
seo-title: 広告挿入メタデータ
title: 広告挿入メタデータ
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 概要 {#ad-insertion-metadata-overview}

広告リゾルバーが機能するようにするには、Adobe Primetime ad decisioningなどの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

ブラウザーTVSDKには、Adobe Primetime ad decisioningライブラリが含まれています。 Adobe Primetime ad decisioningサーバーからの広告をコンテンツに含めるには、アプリケーションが以下の必要なAuditudeSettings情報を提供する必要があります。

* `mediaID`に含まれている場合、再生されるビデオの一意の識別子です。

   発行者は、ビデオコンテンツと広告情報をAdobe Primetime Ad Decisioningサーバーに送信する際に、mediaIDを割り当てます。 このIDは、Adobe Primetime ad decisioningがサーバーからビデオに関連する広告情報を取得するために使用します。

* （オプション） `defaultMediaId`は、次の条件が満たされた場合に提供される広告を指定します。

   * 広告サーバーへの要求が無効か、コンテンツが正しく設定されていません。
   * Adobe Primetime ad decisioningでデータの反映に遅延が発生している。
   * Adobe Primetime ad decisioningのバックエンドプロセスの1つが正常に機能していないか、使用できません。
   >[!TIP]
   >
   >アドビでは、を使用することをお勧めしま `defaultMediaId`す。

* アドビ `zoneID`が割り当てたユーザーは、会社またはWebサイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

   これらのパラメーターは、ニーズおよび広告プロバイダーのニーズに応じて含めることができます。