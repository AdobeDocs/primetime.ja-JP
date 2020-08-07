---
description: TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成する必要があります。このResource Loaderは、FairPlay Streamingサーバーにライセンス取得要求を送信します。
seo-description: TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成する必要があります。このResource Loaderは、FairPlay Streamingサーバーにライセンス取得要求を送信します。
seo-title: TVSDKアプリケーションでのApple FairPlay
title: TVSDKアプリケーションでのApple FairPlay
uuid: 4384d379-37cd-46c5-8c25-0cda16bdebb8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---


# TVSDKアプリケーションでのApple FairPlay  {#apple-fairplay-in-tvsdk-applications}

TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成する必要があります。このResource Loaderは、FairPlay Streamingサーバーにライセンス取得要求を送信します。

リソースローダーコードは、次のタスクを行います。

1. ライセンス取得要求の送信先を決定します。
1. リクエストをフォーマットします。
1. サーバーに必要な情報を提供して、サーバーが要求を許可するかどうかを決定できるようにします。

例えば、ExpressPlayを利用したAdobeのPrimetime Cloud DRMを使用している場合、リソースローダーは次の宛先にリクエストを送信します。

```
https://fp-gen.service.expressplay.com
```

リソースローダーはリクエストをフォーマットし、再生を許可するExpressPlayトークンをURLに添付します。 ExpressPlayトークンを取得する際には、考慮する必要のあるオプションがいくつかあります。 これらのオプションは、コンテンツのパッケージ化方法によって決まります。

コンテンツをパッケージ化すると、M3U8マニフェストに `skd:` URLが挿入されます。 エントリの後に、任意のデータをマニフェストに含めることがで `skd:` きます。 このデータをアプリケーションコードで使用して、上記のタスクを完了できます。 例えば、再生中のコンテンツのID `skd:{content_id}` をアプリが特定できるようにして、そのコンテンツの特定の部分のトークンをリクエストできます。 また、例えばを使用して、エンタイトルメントサーバーのURLをハードコードする必要がな `skd:{entitlement_server_url}?cid={content_id}`いようにすることもできます。

再生開始が他のチャネルで既にコンテンツIDを知っている場合は、 `skd:` URLに情報を必要としないことがあります。 2つ目の例は、設定をテストする理想的なソリューションですが、実稼働環境でも使用できます。

>[!TIP]
>
>の形式はユーザが決定し `skd:`ます。

コンテンツはプロトコルを使用して取得されますが、ライセンスリクエストには `skd:` が使用され `https:`ます。 これらのプロトコルを処理する最も一般的なオプションは次のとおりです。

* **エンドツーエンド再生の初期テスト** コンテンツをパッケージ化する場合は、 `skd:` URLを選択します。 アプリケーションをテストする場合は、ExpressPlayからライセンスを手動で取得し、ローダでライセンス( `https:` URL)とコンテンツURLをハードコードします。

   例：

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **その他のほとんどの場合** 。コンテンツをパッケージ化する場合は、コンテンツのIDを一意に表す `skd:` URLを選択します。 ローダでURLを解析し、サーバに送信してトークンを取得し、生成されたトークンをURLとして使用します。 `skd:`

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

1. FairPlay用のCustomer Resource Loaderは、を実装して作成し `PTAVAssetResourceLoaderDelegate`ます。

   詳しくは、TVSDKアプリケーションでの [Apple FairPlayを参照してください](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)。

   >[!NOTE]
   >
   >『 *FairPlay Streamingプログラムガイド* 』(FairPlayStreaming_PG.pdf *)の手順に従っていることを確認してください。この手順は、* FPS対応アプリケーション開発用の [](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)FairPlay Server SDKに含まれています。

   この `resourceLoader:shouldWaitForLoadingOfRequestedResource` メソッドは、のメソッドと同じで `AVAssetResourceLoaderDelegate`す。

   >[!IMPORTANT]
   >
   >ExpressPlayライセンスサーバーシナリオでは、コンテンツを再生するには、ExpressPlay FairPlayサーバーライセンスリクエストURLをからに変更し `skd://` ます(または `https://``https://`)。

1. FairPlay *Customer* Resource Loaderをに登録 `registerPTAVAssetResourceLoader`します。

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

独自のFairPlayライセンスサーバーを作成した場合、またはサードパーティのFairPlayライセンスサーバーを使用している場合は、ライセンスサーバーのURL、形式、その他の要件を判断するために、ライセンスサーバーのベンダーに問い合わせてください。