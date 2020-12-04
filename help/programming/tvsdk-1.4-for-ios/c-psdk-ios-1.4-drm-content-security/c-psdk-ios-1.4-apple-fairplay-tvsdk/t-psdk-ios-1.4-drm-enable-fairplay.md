---
description: AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。
seo-description: AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。
seo-title: TVSDKアプリケーションでのApple FairPlayの有効化
title: TVSDKアプリケーションでのApple FairPlayの有効化
uuid: fafffdb9-09f9-45fb-9957-3c6e95ed55f9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---


# TVSDKアプリケーションでApple FairPlayを有効にする{#enable-apple-fairplay-in-tvsdk-applications}

AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。

1. `PTAVAssetResourceLoaderDelegate`を実装して、FairPlay Customer Resource Loaderを作成します。

   詳しくは、[TVSDKアプリケーションでのApple FairPlay](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)を参照してください。

   >[!NOTE]
   >
   >[fps対応アプリを開発するFairPlay Server SDKの&#x200B;*FairPlayストリーミングプログラムガイド*(*FairPlayStreaming_PG.pdf*)の手順に従っていることを確認してください。](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)

   `resourceLoader:shouldWaitForLoadingOfRequestedResource`メソッドは、`AVAssetResourceLoaderDelegate`内のメソッドと同じです。

   >[!IMPORTANT]
   >
   >ExpressPlayライセンスサーバーシナリオでは、コンテンツを再生するには、ExpressPlay FairPlayサーバーライセンスリクエストURLを`skd://`から`https://`（または`https://`）に変更します。

1. *FairPlay* Customer Resource Loaderを`registerPTAVAssetResourceLoader`に登録します。

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

独自のFairPlayライセンスサーバーを作成した場合、またはサードパーティのFairPlayライセンスサーバーを使用している場合は、ライセンスサーバーのURL、形式、その他の要件を判断するために、ライセンスサーバーのベンダーに問い合わせてください。
