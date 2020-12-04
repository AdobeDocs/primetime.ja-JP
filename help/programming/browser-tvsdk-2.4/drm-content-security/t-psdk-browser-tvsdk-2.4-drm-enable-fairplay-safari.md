---
description: Primetime DRM Cloud（ExpressPlayを利用）を使用する場合は、FairPlayをSafari向けに有効にすることができます。
seo-description: Primetime DRM Cloud（ExpressPlayを利用）を使用する場合は、FairPlayをSafari向けに有効にすることができます。
seo-title: FairPlayをSafari HLSで有効にする
title: FairPlayをSafari HLSで有効にする
uuid: 6a250a31-cc4b-4c4b-b1e9-893ee3ca5d78
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# Safari HLS用にFairPlayを有効にする{#enable-fairplay-for-safari-hls}

Primetime DRM Cloud（ExpressPlayを利用）を使用する場合は、FairPlayをSafari向けに有効にすることができます。

次の事項を確認します。

* HLSビデオを再生できる機能的なサンプルアプリです。

   サンプルアプリで、FairPlayで保護されたコンテンツを、ExpressPlayを使用するPrimetime DRM経由で処理されたライセンスと共に再生できる必要があります。
* FairPlay保護がパッケージ化されたサンプルHLSコンテンツ（M3U8マニフェスト）。

この情報を十分に活用するために、[Reference Serverのサブセクションで始まるMulti-DRMワークフローについて学びます。Multi-DRMワークフローガイドのExpressPlay Entitlement Server(SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf)の例を参照してください。 まず、エンタイトルメントとキーサーバーの設定方法に関するドキュメントを読んでください。以下の情報がより役に立ちます。
次のアイテムが必要です。

* ExpressPlayからの&#x200B;*本番環境*&#x200B;ユーザー認証子
* コンテンツがパッケージ化されたのと同じコンテンツキーと`iv`です。
* FairPlay公開鍵証明書の場所です。

FairPlay/Safariアプリケーションを変更するには：

1. FairPlayライセンスサーバーリクエストで使用されたFairPlay公開鍵証明書の場所を設定します。

   例：

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. ExpressPlayに対して手動のFairPlayライセンス&#x200B;*トークン*&#x200B;リクエストを実行し、ライセンストークンURLを取得します。

       この手順は、次のいずれかの方法で実行できます。
   
   * 独自のExpressPlay実稼働用ユーザー認証子を使用します。
   * 再生するコンテンツのパッケージ化に使用したのと同じコンテンツキーと`iv`をこの要求で使用します。

      シェルから次のコマンドを実行し、ExpressPlayのユーザー認証子を置き換えて、サンプルコンテンツのライセンストークンURLを取得します。

      ```
      curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
           customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
           errorFormat=json& 
           contentKey=<your content key>& 
           iv=<your iv here>"
      ```

      ライセンストークンURLを含むレスポンスは次のようになります。

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

1. アプリで保護されたコンテンツを再生できるようにするには、コンテンツのURLスキームを`skd://`から`https://`に変更します。

   再生を許可するライセンスサーバーを呼び出す前に、アプリにこのURLスキームの変更を追加する必要があります。

   キー管理システムのコンテンツキーへのアクセスを提供するコンテンツIDは、M3U8マニフェスト内に`skd://`プロトコルと共にパッケージ化されているので、プロトコルを変更する必要があります。 プレイヤーが保護されたコンテンツを再生するためのライセンスを取得する準備ができたら、まず、ExpressPlayライセンスサーバーと通信するためのプロトコルを切り替える必要があります。 次の例では、`myServerProcessSPCPath`が、ライセンスサーバー要求に対する正しいURLスキームを含むように変更されています。

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

