---
description: AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。
seo-description: AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。
seo-title: TVSDKアプリケーションでのApple FairPlayの有効化
title: TVSDKアプリケーションでのApple FairPlayの有効化
uuid: fafffdb9-09f9-45fb-9957-3c6e95ed55f9
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TVSDKアプリケーションでのApple FairPlayの有効化{#enable-apple-fairplay-in-tvsdk-applications}

AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。

1. FairPlayカスタマーリソースローダーを作成するには、を実装しま `PTAVAssetResourceLoaderDelegate`す。

   詳しくは、TVSDKアプリケーションでの [Apple FairPlayを参照してください](../../c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)。

   >[!NOTE]
   >
   >『 *FairPlay Streaming Program Guide* ( *FairPlayStreaming_PG.pdf*)』(FPS対応アプリの開発用の [FairPlay Server SDKに含まれている)の手順に従ってください](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)。

   この方 `resourceLoader:shouldWaitForLoadingOfRequestedResource` 法は、のと同じです `AVAssetResourceLoaderDelegate`。

   >[!IMPORTANT] {importance=&quot;high&quot;}
   >
   >ExpressPlayライセンスサーバーシナリオでは、コンテンツを再生するには、ExpressPlay FairPlayサーバーライセンスリクエストURLのURLスキームをからに変 `skd://` 更(また `https://` は `https://`)します。

1. FairPlay Customer Resource Loader *をに登録します*`registerPTAVAssetResourceLoader`。

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

独自のFairPlayライセンスサーバーを作成した場合、またはサードパーティのFairPlayライセンスサーバーを使用している場合は、ライセンスサーバーのベンダーに問い合わせて、ライセンスサーバーのURL、形式、その他の要件を確認してください。
