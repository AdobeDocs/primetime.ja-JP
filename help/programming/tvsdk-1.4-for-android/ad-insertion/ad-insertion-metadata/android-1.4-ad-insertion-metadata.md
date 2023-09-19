---
description: 広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。
title: 広告挿入メタデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# 概要 {#ad-insertion-metadata}

広告リゾルバーを機能させるには、Adobe Primetime Ad Decisioning などの広告プロバイダーが、プロバイダーへの接続を有効にするために設定値を必要とします。

TVSDK には、 Primetime ad decisioning ライブラリが含まれています。 コンテンツに Primetime ad decisioning サーバーからの広告を含めるには、アプリケーションが次の必要事項を提供する必要があります `AuditudeSettings` 情報：

* `mediaID`：再生するビデオの一意の識別子です。

  発行者が `mediaID` ビデオコンテンツと広告情報をAdobe Primetime ad decisioning サーバーに送信する際に使用します。 この ID は、Primetime ad decisioning がビデオに関連する広告情報をサーバーから取得するために使用します。

* （オプション） `defaultMediaId`：以下の条件を満たした場合に提供される広告を指定します。

   * 広告サーバーへのリクエストが無効か、コンテンツが正しく設定されていません。
   * Primetime Ad Decisioning によるデータの伝播に遅延が発生しています。
   * Primetime ad decisioning のバックエンドプロセスの 1 つが正常に機能しないか、使用できません。

  >[!TIP]
  >
  >Adobeは、 `defaultMediaId`.

* お使いの `zoneID`:Adobeによって割り当てられ、会社または Web サイトを識別します。
* 割り当てられた広告サーバーのドメイン。
* その他のターゲティングパラメーター。

  広告プロバイダーのニーズやニーズに応じて、これらのパラメーターを含めることができます。
