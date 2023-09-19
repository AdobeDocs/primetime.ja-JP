---
description: Primetime デジタル著作権管理 (DRM) システムの主なクライアント側要素は DRM マネージャーです。
title: Primetime DRM インターフェイスの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Primetime DRM インターフェイスの概要{#primetime-drm-interface-overview}

Primetime デジタル著作権管理 (DRM) システムの主なクライアント側要素は DRM マネージャーです。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM は、TVSDK アプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツに対する権限を保護および管理できます。

TVSDK は、カスタム DRM ワークフローとして Primetime DRM 統合をサポートしています。 つまり、Flash `DRMManager`. これを有効にするには、 `MediaPlayer` は、認証用の DRM マネージャーを提供します。

DRM を操作するための最も重要な API 要素は次のとおりです。

* DRM サブシステムを実装する DRM マネージャーオブジェクトへのメディアプレーヤー内の参照。

  ```
  public function get drmManager():DRMManager 
  ```

<!--<a id="section_4204CE2731A44F67A3664AEDE8CCCA47"></a>-->

関連するその他の API エレメント：

* [flash.net.drm.DRMManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html)
* [flash.net.drm.DRMContentData](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMContentData.html)
* [flash.net.drm.DRMVoucher](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMVoucher.html)
* [flash.net.drm.AuthenticationMethod](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/AuthenticationMethod.html)
* [flash.events.DRMStatusEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMStatusEvent.html)
* [flash.events.DRMErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMErrorEvent.html)

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

DRM について詳しくは、 Adobe Primetime DRM のドキュメントを参照してください。
