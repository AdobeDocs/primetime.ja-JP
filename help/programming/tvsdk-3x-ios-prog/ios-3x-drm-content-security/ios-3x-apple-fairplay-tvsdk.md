---
description: TVSDK アプリに FairPlay ストリーミングを実装するには、Resource Loader を記述する必要があります。この Resource Loader は、FairPlay ストリーミングサーバにライセンス取得要求を送信します。
title: TVSDK アプリケーションでのApple FairPlay
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# TVSDK アプリケーションでのApple FairPlay {#apple-fairplay-in-tvsdk-applications}

TVSDK アプリに FairPlay ストリーミングを実装するには、Resource Loader を記述する必要があります。この Resource Loader は、FairPlay ストリーミングサーバにライセンス取得要求を送信します。

リソースローダーコードは、次のタスクを担当します。

1. ライセンス取得リクエストの送信先を決定します。
1. リクエストの形式を設定します。
1. サーバに必要な情報を提供し、サーバが要求を許可するかどうかを決定できるようにします。

例えば、ExpressPlay を利用したAdobeの Primetime Cloud DRM を使用している場合、リソースローダーは次の宛先にリクエストを送信します。

```
https://fp-gen.service.expressplay.com
```

リソースローダーは、リクエストをフォーマットし、URL への再生を許可する ExpressPlay トークンを付加します。 ExpressPlay トークンを取得する際には、考慮すべきオプションがいくつかあります。 これらのオプションは、コンテンツのパッケージ化方法によって決まります。

コンテンツをパッケージ化すると、Packager が `skd:` M3U8 マニフェスト内の URL。 次の期間の後に `skd:` エントリの場合は、任意のデータをマニフェストに配置できます。 このデータをアプリケーションコードで使用して、上記のタスクを完了できます。 例えば、 `skd:{content_id}` 再生されているコンテンツの ID をアプリが特定し、そのコンテンツの特定の部分に対してトークンをリクエストできるようにします。 また、例えば、 `skd:{entitlement_server_url}?cid={content_id}`を使用することで、アプリで使用する際に、使用権限サーバーの URL をハードコードする必要がなくなります。

情報が不要な場合は、 `skd:` URL （再生が開始したときに、他のチャネルを通じて既にコンテンツ ID がわかっている場合）。 2 つ目の例は、設定をテストする最適なソリューションですが、実稼働環境でも使用できます。

>[!TIP]
>
>次の形式を決定します。 `skd:`.

コンテンツは、 `skd:` プロトコルを使用していますが、ライセンスリクエストがを使用しています `https:`. これらのプロトコルに対処する最も一般的なオプションを次に示します。

* **エンドツーエンド再生の初期テスト** コンテンツをパッケージ化する際に、 `skd:` URL。 アプリをテストする場合、ExpressPlay からライセンスを手動で取得し、ライセンスをハードコードします ( `https:` URL) およびコンテンツ URL を使用して読み込むことができます。

  例：

  ```
  NSString* const PLAYLIST_URL =  
    @"https://{your_content_URL}/{your_manifest}.m3u8"; 
  NSString* const EXPRESSPLAY_TOKEN =  
    @"https://fp.service.expressplay.com:80/hms/fp/rights/? 
      ExpressPlayToken={copy_your_token_to_here}";
  ```

* **その他のほとんどの場合** コンテンツをパッケージ化する際に、 `skd:` コンテンツの ID を一意に表す URL。 ローダーで、 `skd:` URL を作成し、それをサーバーに送信してトークンを取得し、生成されたトークンを URL として使用します。

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

## TVSDK アプリケーションでのApple FairPlay の有効化 {#section_61CFA3C22FE64F52B2C8CE860B72E88B}

Appleの DRM ソリューションであるApple FairPlay Streaming を TVSDK アプリケーションに実装できます。

1. を実装して FairPlay カスタマーリソースローダーを作成する `PTAVAssetResourceLoaderDelegate`. 詳しくは、 TVSDK アプリケーションでのApple FairPlay を参照してください。

   >[!NOTE]
   >
   >必ず *FairPlay ストリーミングプログラムガイド* ( *FairPlayStreaming_PG.pdf*) に含まれます。 [FPS 対応アプリを開発するための FairPlay Server SDK](https://developer.apple.com/services-account/download?path=/Developer_Tools/FairPlay_Streaming_SDK/FairPlay_Streaming_Server_SDK.zip)) をクリックします。

   メソッド `resourceLoader:shouldWaitForLoadingOfRequestedResource` は、 `AVAssetResourceLoaderDelegate`.

   >[!NOTE]
   >
   >ExpressPlay ライセンスサーバーのシナリオで、コンテンツを再生するには、ExpressPlay FairPlay サーバーライセンスリクエスト URL を次の場所から変更します。 `skd://` から `https://` ( または `https://`) をクリックします。

1. を登録します。 *FairPlay* 次を使用した顧客リソースローダー `registerPTAVAssetResourceLoader`.

   ```
   PTFairPlayResourceLoader *resourceLoader =  
     [[PTFairPlayResourceLoader new] autorelease];  
   [[PTDefaultMediaPlayerClientFactory defaultFactory]  
     registerPTAVAssetResourceLoader:resourceLoader];
   ```

   >[!NOTE]
   >
   >独自の FairPlay ライセンスサーバを作成した場合、またはサードパーティの FairPlay ライセンスサーバを使用している場合は、ライセンスサーバのベンダーに問い合わせて、ライセンスサーバの URL、形式、その他の要件を確認してください。
