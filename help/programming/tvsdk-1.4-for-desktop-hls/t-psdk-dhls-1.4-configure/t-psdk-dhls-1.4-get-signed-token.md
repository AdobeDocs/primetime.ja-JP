---
description: FlashRuntime TVSDK では、署名付きトークンが必要です。このトークンを使用して、アプリケーションが存在するドメイン上で TVSDK API を呼び出す権限があることを検証できます。
title: 署名付きトークンを読み込む
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 署名付きトークンを読み込む {#load-your-signed-token}

FlashRuntime TVSDK では、署名付きトークンが必要です。このトークンを使用して、アプリケーションが存在するドメイン上で TVSDK API を呼び出す権限があることを検証できます。

1. 各ドメインのAdobe担当者から署名付きトークンを取得します（各ドメインは、特定のドメインまたはワイルドカードドメインになります）。

       トークンを取得するには、Adobeに、アプリケーションが保存または読み込まれるドメインか、できればドメインを SHA256 ハッシュとして指定します。 その代わり、Adobeは各ドメインに対して署名付きトークンを提供します。 これらのトークンは、次のいずれかの形式を取ります。
   
   * An [!DNL .xml] 単一のドメインまたはワイルドカードドメインのトークンとして機能するファイル。

     >[!NOTE]
     >
     >ワイルドカードドメインのトークンは、そのドメインとそのすべてのサブドメインをカバーします。 例えば、ドメインのワイルドカードトークン [!DNL mycompany.com] また、カバーする [!DNL vids.mycompany.com] および [!DNL private.vids.mycompany.com]；のワイルドカードトークン [!DNL vids.mycompany.com] また、カバーする [!DNL private.vids.mycompany.com]. *ワイルドカードドメイントークンは、特定のバージョンのFlash Playerでのみサポートされます。*

   * A [!DNL .swf] 複数のドメイン（ワイルドカードを含まない）（単一またはワイルドカード）のトークン情報を含むファイル。アプリケーションは動的に読み込むことができます。

1. トークンファイルは、アプリケーションと同じ場所またはドメインに保存します。

   デフォルトでは、 TVSDK はこの場所でトークンを探します。 または、でトークンの名前と場所を指定できます。 `flash_vars` をHTMLファイルに追加します。
1. トークンファイルが単一の XML ファイルの場合：
   1. 用途 `utils.AuthorizedFeaturesHelper.loadFrom` ：指定した URL（トークンファイル）に保存されたデータをダウンロードし、 `authorizedFeatures` 情報を送信します。

      この手順は異なる場合があります。 例えば、アプリケーションを起動する前に認証を実行したり、コンテンツ管理システム (CMS) から直接トークンを受け取ったりすることができます。

   1. TVSDK が `COMPLETED` イベント（読み込みが成功した場合）、または `FAILED` イベントを設定しません。 いずれかのイベントを検出したら、適切なアクションを実行します。

      アプリケーションが必要なを提供するには、これを成功させる必要があります `authorizedFeatures` オブジェクトを TVSDK に `MediaPlayerContext`.

   次の例では、単一のトークンを使用する方法を示します [!DNL .xml] ファイル。

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

1. トークンが [!DNL .swf] ファイル：
   1. を定義 `Loader` 動的に読み込むクラス [!DNL .swf] ファイル。
   1. を設定します。 `LoaderContext` ：現在のアプリケーションドメインに読み込みを指定する場合。これにより、 TVSDK は、 [!DNL .swf] ファイル。 次の場合 `LoaderContext` が指定されていない場合、 `Loader.load` は、現在のドメインの子ドメインに.swf を読み込みます。
   1. COMPLETE イベントをリッスンします。このイベントは、読み込みが成功した場合に TVSDK がディスパッチします。

      また、ERROR イベントをリッスンし、適切なアクションを実行します。
   1. 読み込みが成功した場合は、 `AuthorizedFeaturesHelper` 手に入れる `ByteArray` PCKS-7 でエンコードされたセキュリティデータを含む

      このデータは、AVE V11 API を通じて、FlashRuntime Player から認証確認を取得するために使用されます。 バイト配列にコンテンツがない場合は、代わりに、単一ドメイントークンファイルを探す手順を使用します。
   1. 用途 `AuthorizedFeatureHelper.loadFeatureFromData` 必要なデータをバイト配列から取得します。
   1. をアンロードします。 [!DNL .swf] ファイル。

   次の例は、複数トークンの使用方法を示しています [!DNL .swf] ファイル。

   **複数トークンの例 1:**

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

   **複数トークンの例 2:**

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
