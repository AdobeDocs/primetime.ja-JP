---
description: Primetime DRM Cloudを使用している場合、ExpressPlayを利用してFairPlayをSafariで有効にすることができます。
seo-description: Primetime DRM Cloudを使用している場合、ExpressPlayを利用してFairPlayをSafariで有効にすることができます。
seo-title: Safari HLSでFairPlayを有効にする
title: Safari HLSでFairPlayを有効にする
uuid: 6a250a31-cc4b-4c4b-b1e9-893ee3ca5d78
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# Safari HLSでFairPlayを有効にする {#enable-fairplay-for-safari-hls}

Primetime DRM Cloudを使用している場合、ExpressPlayを利用してFairPlayをSafariで有効にすることができます。

次の事項を確認します。

* HLSビデオを再生できる機能的なサンプルアプリ。

   サンプルアプリは、FairPlayで保護されたコンテンツを、ExpressPlayを使用するPrimetime DRMを通じて処理されたライセンスで再生できる必要があります。
* FairPlay保護でパッケージ化されたHLSコンテンツ（M3U8マニフェスト）の例。

この情報をフルに活用するには、サブセクションリファレンスサーバーから始まるMulti-DRMワークフローにつ [いて説明します。Multi-DRMワークフローガイドのExpressPlay Entitlement Server(SEES)の例を参照してください](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) 。 まず、エンタイトルメントとキーサーバーの設定方法に関するドキュメントを読んでください。以下の情報がより役に立ちます。
次の項目が必要です。

* ExpressPlayか *らの* Production Customer Authenticator
* コンテンツがパッケージ化さ `iv` れたのと同じコンテンツキー。
* FairPlay公開鍵証明書の場所です。

FairPlay/Safariアプリケーションを変更するには：

1. FairPlayライセンスサーバー要求で使用されたFairPlay公開鍵証明書の場所を設定します。

   例：

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. ExpressPlayに対して手動のFairPlayライセ *ンストークン* リクエストを実行し、ライセンストークンURLを取得します。

       この手順は、次のいずれかの方法で実行できます。
   
   * 独自のExpressPlay実稼働ユーザー認証子を使用します。
   * 再生するコンテンツのパッケ `iv` ージ化に使用したのと同じコンテンツキーと、この要求で使用します。

      シェルから次のコマンドを実行し、ExpressPlayの顧客認証子を置き換えて、サンプルコンテンツのライセンストークンURLを取得します。

      ```
      curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
           customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
           errorFormat=json& 
           contentKey=<your content key>& 
           iv=<your iv here>"
      ```

      ライセンストークンのURLを含む応答は次のようになります。

      ```
      https://fp.service.expressplay.com:80/hms/fp/rights/? 
           ExpressPlayToken=<base64-encoded ExpressPlay token>
      ```

1. ExpressPlayのライセンストークンURLを使用して変数を設定します。

   例：

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. アプリで保護されたコンテンツを再生する前に、コンテンツのURLスキームをからに変更 `skd://` しま `https://`す。

   再生を許可するライセンスサーバーを呼び出す前に、アプリでこのURLスキームの変更を追加する必要があります。

   プロトコルは変更する必要があります。これは、Key Management Systemのコンテンツキーへのアクセスを提供するコンテンツIDが、プロトコルと共にM3U8マニフェストにパッケージ化されているから `skd://` です。 保護されたコンテンツを再生するライセンスを取得する準備が整ったら、まずExpressPlayライセンスサーバーと通信するためにプロトコルを切り替える必要があります。 次の例では、ライセンスサ `myServerProcessSPCPath` ーバーリクエストの正しいURLスキームを含むようにに変更します。

   ```js
   extractContentId(initData) {  
       contentId = arrayToString(initData); // contentId is passed up as a URI,  
                                            // from which the host must be extracted:  
       var link = document.createElement('a');  
       link.href = contentId;  
       var index = contentId.indexOf(':');  
       myServerProcessSPCPath = "https:" + contentId.substring(index+1);  
       console.log("severProcessSPCPAth = " + serverProcessSPCPath); return link.hostname;  
   }
   ```

