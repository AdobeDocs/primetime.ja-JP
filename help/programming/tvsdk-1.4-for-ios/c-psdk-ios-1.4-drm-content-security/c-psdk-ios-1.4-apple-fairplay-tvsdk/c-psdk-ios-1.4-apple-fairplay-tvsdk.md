---
description: TVSDKアプリにFairPlay Streamingを実装するには、Resource Loaderを作成する必要があります。このResource Loaderは、FairPlay Streamingサーバーにライセンス取得要求を送信します。
title: TVSDKアプリケーションでのApple FairPlay
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# TVSDKアプリケーションでのApple FairPlay {#apple-fairplay-in-tvsdk-applications}

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

コンテンツをパッケージ化すると、PackagerがM3U8マニフェストに`skd:` URLを挿入します。 `skd:`エントリの後に、マニフェストに任意のデータを配置できます。 このデータをアプリケーションコードで使用して、上記のタスクを完了できます。 例えば、`skd:{content_id}`を使用して、再生中のコンテンツのIDをアプリが特定し、そのコンテンツのトークンをリクエストできるようにします。 また、例えば`skd:{entitlement_server_url}?cid={content_id}`を使用すると、アプリにエンタイトルメントサーバーのURLをハードコードする必要がなくなります。

再生開始が他のチャネルーで既にコンテンツIDを知っている場合は、`skd:` URLに何も情報を必要としないことがあります。 2つ目の例は、設定をテストする理想的なソリューションですが、実稼働環境でも使用できます。

>[!TIP]
>
>`skd:`の形式を決定します。

コンテンツは`skd:`プロトコルを使用して取得されますが、ライセンスリクエストには`https:`が使用されています。 これらのプロトコルを処理する最も一般的なオプションは次のとおりです。

* **エンドツーエンド** 再生の初期テストコンテンツのパッケージ化時に、 `skd:` URLを選択します。アプリケーションをテストする場合は、ExpressPlayからライセンスを手動で取得し、ローダ内のライセンス(`https:` URL)とコンテンツURLをハードコードします。

   例：

   ```
   NSString* const PLAYLIST_URL =  
     @"https://{your_content_URL}/{your_manifest}.m3u8"; 
   NSString* const EXPRESSPLAY_TOKEN =  
     @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
       ExpressPlayToken={copy_your_token_to_here}";
   ```

* **その他のほとんどの** 場合コンテンツのパッケージ化を行う場合は、コンテンツのIDを一意に表す `skd:` URLを選択します。ローダで`skd:` URLを解析し、サーバに送信してトークンを取得し、結果のトークンをURLとして使用します。

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

## TVSDKアプリケーションでApple FairPlayを有効にする{#enable-apple-fairplay-in-tvsdk-applications}

AppleのDRMソリューションであるApple FairPlay StreamingをTVSDKアプリケーションに実装できます。

1. `PTAVAssetResourceLoaderDelegate`を実装して、FairPlay Customer Resource Loaderを作成します。

   詳しくは、[TVSDKアプリケーションでのApple FairPlay](../../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-drm-content-security/c-psdk-ios-1.4-apple-fairplay-tvsdk/c-psdk-ios-1.4-apple-fairplay-tvsdk.md)を参照してください。

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