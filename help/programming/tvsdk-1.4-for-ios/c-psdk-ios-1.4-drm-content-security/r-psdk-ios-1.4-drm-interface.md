---
description: Primetimeデジタル著作権管理(DRM)システムのクライアント側の主要な要素は、DRMマネージャーです。
seo-description: Primetimeデジタル著作権管理(DRM)システムのクライアント側の主要な要素は、DRMマネージャーです。
seo-title: Primetime DRMインターフェイスの概要
title: Primetime DRMインターフェイスの概要
uuid: 3aae7c7a-fd0c-430e-9018-fd72801ab778
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# Primetime DRMインターフェイスの概要 {#primetime-drm-interface-overview}

Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。

サードパーティのDRMソリューションの可用性に関する最新情報については、アドビの担当者にお問い合わせください。

Primetimeデジタル著作権管理(DRM)システムのクライアント側の主要な要素は、DRMマネージャーです。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

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

>[!TIP] {importance=&quot;high&quot;}
>
>DRM保護されたアセットURLをiOSアプリで参照する場合、クエリ文字列パラメーターを(MBR) `?faxs=1` セットレベルのM3U8 URLに追加する必要があります。 例：>
>
```>
>https://your.domain.com/hls/[...]/index.m3u8?faxs=1
>```>
>The `faxs=1` query string parameter signals that the content is DRM protected, and triggers the DRM decryption workflow accordingly in the iOS TVSDK. You can also append the `faxs=1` tag on DRM-protected HLS asset URLs that are destined for other platforms; it is observed as required on iOS or treated as a non-op in players on other platforms.



<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

DRMについて詳しくは、 [Adobe Primetime DRMのドキュメントを参照してください](https://help.adobe.com/en_US/primetime/drm)。

## TSVDKアプリケーションでのPrimetime DRMの実装 {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRMはTVSDKに統合され、TVSDKアプリケーションでのコンテンツ保護の実装を簡単にします。

Primetime DRMを使用してTVSDKアプリケーションにコンテンツ保護を実装する方法の概要と詳細については、次を参照してください。

* [Adobe Primetime TVSDK-DRMワークフロー(PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)