---
description: FlashランタイムTVSDKは、署名付きトークンを必要とします。このトークンを使用して、アプリケーションが存在するドメインでTVSDK APIを呼び出す権限があることを検証します。
title: 署名付きトークンの読み込み
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# 署名付きトークン{#load-your-signed-token}を読み込みます

FlashランタイムTVSDKは、署名付きトークンを必要とします。このトークンを使用して、アプリケーションが存在するドメインでTVSDK APIを呼び出す権限があることを検証します。

1. 各ドメイン（各ドメインが特定のドメインまたはワイルドカードドメインの場合がある）に関する署名付きトークンをAdobeの担当者から取得します。

       トークンを取得するには、Adobeに、アプリケーションが保存または読み込まれるドメインか、できればドメインをSHA256ハッシュとして提供します。その代わりに、Adobeから各ドメインに対して署名付きトークンが提供されます。 これらのトークンは、次のいずれかの形式を取ります。
   
   * 単一のドメインまたはワイルドカードドメインのトークンとして機能する[!DNL .xml]ファイル。

      >[!NOTE]
      >
      >ワイルドカードドメインのトークンは、そのドメインとそのすべてのサブドメインをカバーします。 例えば、ドメイン[!DNL mycompany.com]のワイルドカードトークンは、[!DNL vids.mycompany.com]と[!DNL private.vids.mycompany.com]もカバーします。[!DNL vids.mycompany.com]のワイルドカードトークンは、[!DNL private.vids.mycompany.com]もカバーします。 *ワイルドカードドメイントークンは、特定のFlash Playerバージョンに対してのみサポートされます。*

   * 複数のドメイン（ワイルドカードを含まない）（単一ドメインまたはワイルドカードを含む）のトークン情報を含む[!DNL .swf]ファイル。アプリケーションは動的に読み込むことができます。

1. アプリケーションと同じ場所またはドメインにトークンファイルを保存します。

   デフォルトでは、TVSDKはこの場所でトークンを探します。 別の方法として、HTMLファイルの`flash_vars`にトークンの名前と場所を指定することもできます。
1. トークンファイルが単一のXMLファイルの場合：
   1. `utils.AuthorizedFeaturesHelper.loadFrom`を使用して、指定したURL（トークンファイル）に保存されているデータをダウンロードし、`authorizedFeatures`情報を抽出します。

      この手順は異なる場合があります。 例えば、アプリケーションを起動する前に認証を実行したり、コンテンツ管理システム(CMS)から直接トークンを受け取ったりする場合があります。

   1. TVSDKは、読み込みが成功した場合は`COMPLETED`イベントをディスパッチし、それ以外の場合は`FAILED`イベントをディスパッチします。 どちらかのイベントを検出したら、適切な対応を行います。

      アプリケーションが必要な`authorizedFeatures`オブジェクトを`MediaPlayerContext`の形式でTVSDKに提供するには、この処理が成功する必要があります。
   次の例は、単一トークンの[!DNL .xml]ファイルを使用する方法を示しています。

   ```
   private function loadDirectTokenURL():void { 
       var url:String = constructAuthorizedFeatureTokenURL(); 
       _logger.debug("#onApplicationComplete Loading token from [{0}].", url); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE,  
           onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR,  
           onFeatureError); 
        _authorizedFeatureHelper.loadFrom(url); 
    }
   ```

1. トークンが[!DNL .swf]ファイルの場合：
   1. `Loader`クラスを定義して、[!DNL .swf]ファイルを動的に読み込みます。
   1. `LoaderContext`を設定して、現在のアプリケーションドメインで読み込みを指定します。これにより、TVSDKは[!DNL .swf]ファイル内で正しいトークンを選択できます。 `LoaderContext`を指定しない場合、`Loader.load`のデフォルトの動作では、現在のドメインの子ドメインにある.swfを読み込みます。
   1. COMPLETEイベントをリッスンします。このイベントは、読み込みが成功した場合にTVSDKがディスパッチします。

      ERRORイベントもリッスンし、適切な処理を行います。
   1. 読み込みが成功した場合は、`AuthorizedFeaturesHelper`を使用して、PCKS-7エンコードされたセキュリティデータを含む`ByteArray`を取得します。

      このデータは、AVE V11 APIを通じて使用され、Flashランタイムプレイヤーから認証確認を取得します。 バイト配列にコンテンツがない場合は、代わりに単一ドメインのトークンファイルを探す手順を使用します。
   1. `AuthorizedFeatureHelper.loadFeatureFromData`を使用して、必要なデータをバイト配列から取得します。
   1. [!DNL .swf]ファイルをアンロードします。

   次の例は、複数トークンの[!DNL .swf]ファイルの使用方法を示しています。

   **複数トークンの例1:**

   ```
   private function onApplicationComplete(event:FlexEvent):void { 
       var url:String = constructAuthorizedFeatureTokenURLFromSwf();   
       _loader = new Loader(); 
       var swfUrl:URLRequest = new URLRequest(url); 
       var loaderContext:LoaderContext =  
           new LoaderContext(false, ApplicationDomain.currentDomain, null); 
       _loader.contentLoaderInfo.addEventListener(Event.COMPLETE,  
           modEventHandler); 
       _loader.contentLoaderInfo.addEventListener(IOErrorEvent.IO_ERROR,  
           errEventHandler); 
       _loader.contentLoaderInfo.addEventListener(ProgressEvent.PROGRESS,  
           onProgressHandler); 
       _loader.uncaughtErrorEvents.addEventListener(UncaughtErrorEvent. 
           UNCAUGHT_ERROR, uncaughtEventHandler); 
       _logger.debug("# Loading token swf with context from [{0}].", url); 
       _loader.load(swfUrl, loaderContext); 
   } 
   
   private function modEventHandler(e:Event):void { 
       _logger.debug("loadSWF with domainID {0}",  
       SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
           loader.contentLoaderInfo.applicationDomain. 
           getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       _authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       _authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       _authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray = myTokens. 
           FetchToken(SecurityDomain.currentDomain.domainID); 
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           _logger.debug("token bytearry size {0}", byteArray.length); 
           _authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   ```

   **複数トークンの例2:**

   ```
   private function tokenSwfLoadedHandler(e:Event):void { 
       trace("loadSWF with domainID {0}", SecurityDomain.currentDomain.domainID); 
       var loader : Loader = e.currentTarget.loader as Loader; 
       var myAuthorizedTokensLoaderClass:Class =  
         loader.contentLoaderInfo.applicationDomain. 
         getDefinition("AuthorizedTokensLoader") as Class; 
       var myTokens:Object = new myAuthorizedTokensLoaderClass(); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       var byteArray:ByteArray =  
           myTokens.FetchToken(SecurityDomain.currentDomain.domainID); 
       var myDomains:Array = ["domain.com"]; 
       if (byteArray == null || byteArray.length == 0) { 
           // check for wildcard tokens 
           if (myTokens.hasOwnProperty("FetchWildCardToken") == true) { 
               // contains wildcard domains 
               for each (var domain:String in myDomains) { 
                   byteArray = myTokens.FetchWildCardToken(domain); 
                   if (byteArray != null && byteArray.length != 0) { 
                       break; 
                   } 
               }; 
           } 
       } 
   
       if (myTokens == null || byteArray == null || byteArray.length == 0) 
           loadDirectTokenURL(); 
       else { 
           trace("token bytearry size {0}", byteArray.length); 
           authorizedFeatureHelper.loadFeatureFromData(byteArray); 
       } 
       _loader.unload(); 
   } 
   
   private function loadDirectTokenURL():void { 
       trace("#onApplicationComplete Loading token from [{0}].", tokenUrl); 
       authorizedFeatureHelper = new AuthorizedFeaturesHelper(); 
       authorizedFeatureHelper.addEventListener(Event.COMPLETE, onFeatureComplete); 
       authorizedFeatureHelper.addEventListener(ErrorEvent.ERROR, onFeatureError); 
       authorizedFeatureHelper.loadFrom(tokenUrl); 
   }
   ```

