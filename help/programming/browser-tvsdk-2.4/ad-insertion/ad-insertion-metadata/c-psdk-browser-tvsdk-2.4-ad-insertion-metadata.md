---
description: 広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
title: 広告挿入メタデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 概要 {#ad-insertion-metadata-overview}

広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

ブラウザー TVSDK には、 Adobe Primetime ad decisioning ライブラリが含まれています。 コンテンツにAdobe Primetime Ad Decisioning サーバーからの広告を含めるには、アプリケーションが以下の必要な AudienceSettings 情報を提供する必要があります。

* `mediaID`：再生するビデオの一意の識別子です。

  公開者は、ビデオコンテンツと広告情報をAdobe Primetime Ad Decisioning サーバーに送信する際に、mediaID を割り当てます。 この ID は、Adobe Primetime Ad Decisioning がビデオに関連する広告情報をサーバーから取得するために使用します。

* （オプション） `defaultMediaId`：以下の条件を満たした場合に提供される広告を指定します。

   * 広告サーバーへのリクエストが無効か、コンテンツが正しく設定されていません。
   * Adobe Primetime ad decisioning で、データの伝播に遅延が発生しています。
   * Adobe Primetime Ad Decisioning のバックエンドプロセスの 1 つが正常に機能しないか、使用できません。

  >[!TIP]
  >
  >Adobeは、 `defaultMediaId`.

* お使いの `zoneID`:Adobeによって割り当てられ、会社または Web サイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

  広告プロバイダーのニーズやニーズに応じて、これらのパラメーターを含めることができます。
