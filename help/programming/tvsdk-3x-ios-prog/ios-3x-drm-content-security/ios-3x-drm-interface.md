---
description: PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合 Primetime DRM ソリューションの代わりに使用することもできます。
keywords: DRM;DASH;HLS
title: Primetime DRM インターフェイスの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Primetime DRM インターフェイスの概要 {#primetime-drm-interface-overview}

PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合 Primetime DRM ソリューションの代わりに使用することもできます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティの DRM ソリューションの入手に関する最新情報については、Adobeの担当者にお問い合わせください。

Primetime デジタル著作権管理 (DRM) システムの主なクライアント側要素は DRM マネージャーです。

Primetime DRM は、TVSDK アプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツに対する権限を保護および管理できます。

TVSDK は、カスタム DRM ワークフローとして Primetime DRM 統合をサポートしています。 つまり、 DRMManagerFlashを使用してストリームを再生する前に、アプリケーションで DRM 認証ワークフローを実装する必要があります。 これを有効にするために、MediaPlayer は認証用の DRM マネージャーを提供します。

TVSDK パッケージに含まれている DRM サンプルプレイヤーコードを参照してください。

DRM を操作するための最も重要な API 要素は次のとおりです。

* DRM サブシステムを実装する DRM マネージャーオブジェクトへのメディアプレーヤー内の参照。

  ```
  @property (readonly, nonatomic) DRMManager *drmManager
  ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK が `PTMediaPlayerItemDRMMetadataChanged` DRM メタデータが変更された場合の通知。 このメタデータは、 `DRMManager` クラス。

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

DRM 保護されたストリームがマルチビットレート (MBR) でエンコードされている場合、バリアントプレイリストに使用される DRM メタデータは、すべてのビットレートストリームで使用されるメタデータと同じである必要があります。

>[!TIP]
>
>DRM で保護されたアセット URL をiOSアプリで参照する場合は、クエリー文字列パラメーター `?faxs=1` は、(MBR) セットレベルの M3U8 URL に追加する必要があります。 例：

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

The `faxs=1` クエリー文字列パラメーターは、コンテンツが DRM 保護されていることを示し、iOS TVSDK でその内容に応じて DRM 復号ワークフローをトリガー化します。 また、 `faxs=1` タグを、他のプラットフォーム向けの DRM 保護された HLS アセット URL に追加します。iOSでは必要に応じて表示されるか、他のプラットフォームでは非 op として扱われます。

## TSVDK アプリケーションへの Primetime DRM の実装 {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM は TVSDK に統合され、TVSDK アプリケーションでのコンテンツ保護の実装を簡単にします。

TVSDK アプリケーションでのコンテンツ保護の実装に Primetime DRM を使用する方法の概要と詳細については、以下を参照してください。

* [Adobe Primetime TVSDK-DRM ワークフロー (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)
