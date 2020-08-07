---
description: PrimetimeDigital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションを、Adobeの統合Primetime DRMソリューションの代替として使用できます。
keywords: DRM;DASH;HLS
seo-description: PrimetimeDigital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションを、Adobeの統合Primetime DRMソリューションの代替として使用できます。
seo-title: Primetime DRMインターフェイスの概要
title: Primetime DRMインターフェイスの概要
uuid: 5e794147-cc58-448c-b8ec-065e80ef01fd
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---


# Primetime DRMインターフェイスの概要 {#primetime-drm-interface-overview}

PrimetimeDigital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションを、Adobeの統合Primetime DRMソリューションの代替として使用できます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティのDRMソリューションの可用性に関する最新情報については、Adobeの担当者にお問い合わせください。

Primetime digital rights management(DRM)システムのクライアント側の主要要素はDRMマネージャーです。

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

TVSDKは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートしています。 つまり、FlashDRMManagerを使用してストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。 これを有効にするために、MediaPlayerは認証用のDRMマネージャーを提供します。

TVSDKパッケージに含まれるDRMサンプルプレイヤーコードを参照してください。

以下は、DRMを操作するための最も重要なAPI要素です。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```
   @property (readonly, nonatomic) DRMManager *drmManager
   ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

DRMメタデータが変更されると、TVSDKは `PTMediaPlayerItemDRMMetadataChanged` 通知を発行します。 このメタデータは、クラスのほとんどすべての関数の入力として使用され `DRMManager` ます。

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

DRM保護されたストリームがマルチビットレート(MBR)でエンコードされている場合、バリアントプレイリストに使用されるDRMメタデータは、すべてのビットレートストリームで使用されるメタデータと同じでなければなりません。

[!TIP]

DRM保護されたアセットのURLをiOSアプリで参照する場合、クエリ文字列パラメーターを(MBR)設定レベルM3U8 URLに追加する `?faxs=1` 必要があります。 例：

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

`faxs=1` クエリ文字列パラメーターは、コンテンツがDRM保護されていることを伝え、それに応じてiOS TVSDKでDRM復号ワークフローをトリガーします。 また、他のプラットフォーム向けのDRM保護されたHLSアセットURLに `faxs=1` タグを追加することもできます。iOSでは必須と見なされるか、他のプラットフォームでは非操作として扱われます。

## TSVDKアプリケーションでのPrimetime DRMの実装 {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRMはTVSDKに統合されているので、TVSDKアプリケーションでのコンテンツ保護の実装を簡略化できます。

Primetime DRMを使用してTVSDKアプリケーションにコンテンツ保護を実装する方法の概要と詳細については、以下を参照してください。

* [Adobe PrimetimeTVSDK-DRMワークフロー(PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)