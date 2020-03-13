---
description: Flash Runtime TVSDKは、署名付きトークンを必要とし、アプリケーションが存在するドメインでTVSDK APIを呼び出す権限があることを検証します。
seo-description: Flash Runtime TVSDKは、署名付きトークンを必要とし、アプリケーションが存在するドメインでTVSDK APIを呼び出す権限があることを検証します。
seo-title: 署名付きトークンの読み込み
title: 署名付きトークンの読み込み
uuid: 8760eab3-3d6d-47c6-9aa7-f64f6aa5ddcf
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# 署名付きトークンの読み込み {#load-your-signed-token}

Flash Runtime TVSDKは、署名付きトークンを必要とし、アプリケーションが存在するドメインでTVSDK APIを呼び出す権限があることを検証します。

1. 各ドメイン（各ドメインが特定のドメインまたはワイルドカードドメインの場合がある）に関する署名付きトークンをアドビの担当者から取得します。

       トークンを取得するには、アプリケーションの格納または読み込み先のドメイン、またはSHA256ハッシュとしてドメインをアドビに提供します。 その代わりに、アドビから各ドメインの署名付きトークンが提供されます。 これらのトークンは、次のいずれかの形式を取ります。
   
   * 単一のド [!DNL .xml] メインまたはワイルドカードドメインのトークンとして機能するファイル。

      >[!NOTE]
      >
      >ワイルドカードドメインのトークンは、そのドメインとそのすべてのサブドメインをカバーします。 例えば、ドメインのワイルドカードトークンは、 [!DNL mycompany.com] およびもカバー [!DNL vids.mycompany.com] します [!DNL private.vids.mycompany.com]。のワイルドカードトーク [!DNL vids.mycompany.com] ンもカバーしま [!DNL private.vids.mycompany.com]す。 *ワイルドカードドメイントークンは、特定のバージョンのFlash Playerに対してのみサポートされます。*

   * 複数のド [!DNL .swf] メイン（ワイルドカードを含まない）（単一またはワイルドカード）のトークン情報を含むファイル。アプリケーションで動的に読み込むことができます。

1. アプリケーションと同じ場所またはドメインにトークンファイルを保存します。

   デフォルトでは、TVSDKはこの場所でトークンを探します。 または、HTMLファイル内でトークンの名前と場所を指 `flash_vars` 定することもできます。
1. トークンファイルが単一のXMLファイルの場合：
   1. 指定し `utils.AuthorizedFeaturesHelper.loadFrom` たURL（トークンファイル）に保存されたデータをダウンロードし、その情報を抽 `authorizedFeatures` 出する場合に使用します。

      この手順は異なる場合があります。 例えば、アプリケーションを起動する前に認証を実行したり、コンテンツ管理システム(CMS)から直接トークンを受け取ったりすることができます。

   1. TVSDKは、読み込みが成功し `COMPLETED` た場合はイベントを、それ以外の場合はイベントを `FAILED` ディスパッチします。 どちらかのイベントを検出したら、適切なアクションを実行します。

      アプリケーションがTVSDKに必要なオブジェクトをTVSDKの形式で提供す `authorizedFeatures` るには、この処理が正常に完了している必要がありま `MediaPlayerContext`す。
   この例では、単一トークンファイルの使用方法を示し [!DNL .xml] ます。

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

1. トークンがファイルの場 [!DNL .swf] 合：
   1. ファイルを動的 `Loader` に読み込むクラスを定義 [!DNL .swf] します。
   1. 読み込みを現 `LoaderContext` 在のアプリケーションドメインに指定するようにを設定します。これにより、TVSDKはファイル内で正しいトークンを選択で [!DNL .swf] きます。 を指 `LoaderContext` 定しない場合、のデフォルトのアクシ `Loader.load` ョンは、現在のドメインの子ドメインに.swfを読み込むことです。
   1. 読み込みが成功した場合にTVSDKがディスパッチするCOMPLETEイベントをリッスンします。

      また、ERRORイベントをリッスンし、適切なアクションを実行します。
   1. 読み込みに成功した場合は、を使用して、PCKS-7 `AuthorizedFeaturesHelper` エンコードさ `ByteArray` れたセキュリティデータを含むを取得します。

      このデータは、AVE V11 APIを通じて、Flash Runtime Playerから認証通知を取得するために使用されます。 バイト配列にコンテンツがない場合は、代わりに単一ドメインのトークンファイルを検索する手順を使用します。
   1. バイト `AuthorizedFeatureHelper.loadFeatureFromData` 配列から必要なデータを取得する場合に使用します。
   1. ファイルをアンロード [!DNL .swf] します。
   次の例は、複数トークンファイルの使用方法を示して [!DNL .swf] います。

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

