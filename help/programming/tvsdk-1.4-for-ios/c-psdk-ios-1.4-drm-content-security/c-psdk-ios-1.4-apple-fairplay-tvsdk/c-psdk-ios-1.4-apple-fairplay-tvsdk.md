---
description: TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成し、FairPlay Streamingサーバにライセンス取得要求を送信する必要があります。
seo-description: TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成し、FairPlay Streamingサーバにライセンス取得要求を送信する必要があります。
seo-title: TVSDKアプリケーションでのApple FairPlay
title: TVSDKアプリケーションでのApple FairPlay
uuid: 4384d379-37cd-46c5-8c25-0cda16bdebb8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TVSDKアプリケーションでのApple FairPlay {#apple-fairplay-in-tvsdk-applications}

TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成し、FairPlay Streamingサーバにライセンス取得要求を送信する必要があります。

リソースローダーコードは、次のタスクを実行します。

1. ライセンス取得要求の送信先を指定します。
1. リクエストをフォーマットします。
1. サーバーに必要な情報を提供し、サーバーが要求を許可するかどうかを決定できるようにします。

例えば、ExpressPlayを利用したAdobeのPrimetime Cloud DRMを使用している場合、リソースローダーは次の宛先にリクエストを送信します。

```
https://fp-gen.service.expressplay.com
```

リソースローダーは、リクエストをフォーマットし、再生を許可するExpressPlayトークンをURLに添付します。 ExpressPlayトークンを取得する際には、考慮すべきオプションがいくつかあります。 これらのオプションは、コンテンツのパッケージ化方法によって決まります。

コンテンツをパッケージ化すると、M3U8マ `skd:` ニフェストにURLが挿入されます。 エントリ `skd:` の後に、任意のデータをマニフェストに含めることができます。 このデータをアプリケーションコードで使用して、上記のタスクを完了できます。 例えば、再生中のコンテ `skd:{content_id}` ンツのIDをアプリが特定できるように、を使用して、そのコンテンツの特定の部分のトークンをリクエストできます。 また、例えば、を使用して、エンタイトルメ `skd:{entitlement_server_url}?cid={content_id}`ントサーバーのURLをハードコードする必要がないようにすることもできます。

再生が始まるときに、他のチャネルを通じてコンテンツIDが既にわかっている場合は、 `skd:` URLに情報が必要ないことがあります。 2つ目の例は、設定をテストする理想的なソリューションですが、実稼働環境でも使用できます。

>[!TIP]
>
>の形式はユーザが決めま `skd:`す。

コンテンツはプロトコルを使用して取得されま `skd:` すが、ライセンス要求ではが使用されま `https:`す。 これらのプロトコルを処理する最も一般的なオプションは、次のとおりです。

* **エンドツーエンド再生の初期テスト** ：コンテンツをパッケージ化する際に、 `skd:` URLを選択します。 アプリケーションをテストする場合は、ExpressPlayからライセンスを手動で取得し、ローダーのライセンス( `https:` URL)とコンテンツURLをハードコードします。

   例：

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **その他のほとんどの場合** 、コンテンツをパッケージ化する場合は、コン `skd:` テンツのIDを一意に表すURLを選択します。 ローダで、URLを解析し、 `skd:` サーバに送信してトークンを取得し、結果のトークンをURLとして使用します。

   例：

   ```
   - (BOOL)resourceLoader:(AVAssetResourceLoader *)resourceLoader  
         shouldWaitForLoadingOfRequestedResource:(AVAssetResourceLoadingRequest *)loadingRequest { 
       NSURL *url = [[loadingRequest request] URL]; 
       if (![[url scheme] isEqual:@"skd"]) 
           return NO; 
   
       NSString *strUrl = [url absoluteString]; 
       NSLog(@"url is: %@", strUrl); 
   
       strUrl = [strUrl stringByReplacingOccurrencesOfString:@"skd://" withString:@"https://"]; 
   
       NSData *assetId; 
   
       NSData *requestBytes; 
       NSError* error = nil; 
       BOOL handled = NO; 
   
       NSData  *responseData = nil; 
   
       assetId = getMyAssetIdentifierFromURL(url); 
   
       /* Usecase 1: "On Premise Fairplay Server" 
        * Set the strUrl to the OnPremise Fairplay Server Url. The OnPremise Fairplay  
        * Server Url is either hardcoded in the App or derived from strUrl. 
        */ 
   #if 0  
       // Insert your use case 1 codes here: 
       // strUrl = getOnPremiseServerUrl(strUrl, assetId); 
   #endif // 
   
       /* Usecase 2: The strUrl is the entitlement server. 
        * Send assetId to the entitlement server; if the user is allowed to playback  
        * the content, the entitlement server will send back an ExpressPlay Token Url. 
        */ 
   
   #if 0 
       // The hardcoded SEES server: 
       strUrl = @"https://10.0.248.85:8080/sees/SEESServlet"; 
   
       // You can use the following code to simulate a device binding entitlement  
       // request:  
       // First, invoke getExpressPlayTokenUrlFromEntilementServer with  
       // bEnforceDeviceID set to false. When you play the content, the device_id  
       // will be registered on the ExpressPlay Server.  Now change code to set  
       // bEnforceDeviceID to true, and rerun the program. The ExpressPlay token  
       // sent back by the SEES server will be device bound. 
   
       // The strUrl returned below is the ExpressPlay Token URL. 
       strUrl = getExpressPlayTokenUrlFromEntilementServer(strUrl, assetId, true, &error); 
   #endif 
   
       /* Usecase 3: The strUrl is already the ExpressPlay Token Url. 
        */ 
   
       // Read in the certificate 
       NSLog(@"Get Application Certificate"); 
       NSString* certPath = [[NSBundle mainBundle] pathForResource:@"my_certificate.cer"  
                                                            ofType:nil]; 
   
       NSData *appCert = [NSData dataWithContentsOfFile:certPath]; 
   
       // To create the request blob for the server: 
       requestBytes = [loadingRequest streamingContentKeyRequestDataForApp: appCert 
                                                         contentIdentifier:assetId  
                                                                   options:nil  
                                                                     error:&error]; 
       if (requestBytes == nil) { 
           NSLog(@"Error creating server request: %@", error); 
           return false; 
       } 
       // Per the specification, send requestBytes along with the assetId to the Key 
       // Server and obtain the response. 
       NSError *err; 
   
       responseData = getCKCFromExpressPlayService( strUrl, requestBytes, assetId, &err); 
   
       if (responseData != nil) { 
           NSLog(@"Get response data: "); 
           [loadingRequest finishLoadingWithResponse:nil  
                                                data:(NSData *)responseData 
                                            redirect:nil]; 
       } 
       else { 
           [loadingRequest finishLoadingWithError:err]; 
           NSLog(@"bad key response"); 
       } 
       handled = YES; 
   bail: 
       return handled; 
   
   }
   ```

## TVSDKアプリケーションでのApple FairPlayの有効化{#enable-apple-fairplay-in-tvsdk-applications}

AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。

1. FairPlayカスタマーリソースローダーを作成するには、を実装しま `PTAVAssetResourceLoaderDelegate`す。

   詳しくは、TVSDKアプリケーションでの [Apple FairPlayを参照してください](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)。

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