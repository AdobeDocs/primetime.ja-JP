---
description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。
keywords: DRM;DASH;HLS
seo-description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。
seo-title: Primetime DRMインターフェイスの概要
title: Primetime DRMインターフェイスの概要
uuid: 5e794147-cc58-448c-b8ec-065e80ef01fd
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Primetime DRMインターフェイスの概要 {#primetime-drm-interface-overview}

Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティのDRMソリューションの可用性に関する最新情報については、アドビの担当者にお問い合わせください。

Primetimeデジタル著作権管理(DRM)システムのクライアント側の主要な要素は、DRMマネージャーです。

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するための、スケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

TVSDKは、Primetime DRM統合をカスタムDRMワークフローとしてサポートしています。 つまり、Flash DRMManagerを使用してストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。 これを有効にするために、MediaPlayerは認証用のDRMマネージャーを提供します。

TVSDKパッケージに含まれているDRMサンプルプレイヤーコードを参照してください。

DRMを操作するための最も重要なAPI要素は次のとおりです。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```
   @property (readonly, nonatomic) DRMManager *drmManager
   ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

DRMメタデータが変更さ `PTMediaPlayerItemDRMMetadataChanged` れると、TVSDKは通知を発行します。 このメタデータは、クラスのほとんどすべての関数の入力として使用さ `DRMManager` れます。

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

DRM保護されたストリームがマルチビットレート(MBR)でエンコードされている場合、バリアントプレイリストに使用されるDRMメタデータは、すべてのビットレートストリームで使用されるメタデータと同じである必要があります。

[!TIP] {importance=&quot;high&quot;}

DRM保護されたアセットURLをiOSアプリで参照する場合、クエリ文字列パラメーターを(MBR) `?faxs=1` セットレベルのM3U8 URLに追加する必要があります。 例：

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

クエリ `faxs=1` 文字列パラメーターは、コンテンツがDRM保護されていることを通知し、それに応じてiOS TVSDKでDRM復号ワークフローをトリガーします。 また、他のプラットフォ `faxs=1` ームを宛先とするDRM保護されたHLSアセットのURLにタグを追加することもできます。iosでは必要に応じて観察され、他のプラットフォームでは非操作として扱われます。

## TSVDKアプリケーションでのPrimetime DRMの実装 {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRMはTVSDKに統合され、TVSDKアプリケーションでのコンテンツ保護の実装を簡単にします。

Primetime DRMを使用してTVSDKアプリケーションにコンテンツ保護を実装する方法の概要と詳細については、次を参照してください。

* [Adobe Primetime TVSDK-DRMワークフロー(PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)