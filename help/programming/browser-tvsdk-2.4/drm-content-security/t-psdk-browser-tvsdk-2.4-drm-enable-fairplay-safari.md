---
description: Primetime DRM Cloud(powered by ExpressPlay) を操作する際に、Safari 用の FairPlay を有効にすることができます。
title: Safari HLS に対する FairPlay の有効化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Safari HLS に対する FairPlay の有効化 {#enable-fairplay-for-safari-hls}

Primetime DRM Cloud(powered by ExpressPlay) を操作する際に、Safari 用の FairPlay を有効にすることができます。

次の点を確認します。

* HLS ビデオを再生できる、機能的なサンプルアプリです。

  サンプルアプリで、FairPlay で保護されたコンテンツを、ExpressPlay を利用した Primetime DRM を通じて処理されたライセンスで再生できる必要があります。
* FairPlay 保護を備えたサンプル HLS コンテンツ（M3U8 マニフェスト）。

この情報を最大限に活用するには、サブセクションから始まる Multi-DRM ワークフローについて学びます [参照サーバー： ExpressPlay 使用権限サーバーの例 (SEES)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_multi_drm_workflows.pdf) （ Multi-DRM ワークフローガイド）を参照してください。 まず、使用権限とキーサーバーの設定方法に関するドキュメントをお読みください。以下の情報がより役に立ちます。
次の項目が必要です。

* お使いの *実稼動* ExpressPlay のユーザー認証
* 同じコンテンツキーおよび `iv` コンテンツをパッケージ化する際に使用します。
* FairPlay 公開鍵証明書の場所。

FairPlay/Safari アプリを変更するには、次の手順を実行します。

1. FairPlay ライセンスサーバーリクエストで使用された FairPlay 公開鍵証明書の場所を設定します。

   例：

   ```js
   var myServerCertificatePath = './my_fairplay.cer';
   ```

1. 手動で FairPlay ライセンスを実行する *トークン* ExpressPlay に対して、ライセンストークン URL の取得をリクエストします。

       この手順は、次のいずれかの方法で実行できます。
   
   * 独自の ExpressPlay 実稼動用ユーザー認証子を使用する。
   * 同じコンテンツキーと `iv` 再生するコンテンツのパッケージ化に使用されたこのリクエスト。

     シェルから次のコマンドを実行し、ExpressPlay の顧客認証子に置き換えて、サンプルコンテンツのライセンストークン URL を取得します。

     ```
     curl -v "https://fp-gen.service.expressplay.com/hms/fp/token? 
          customerAuthenticator=<ExpressPlay customer authenticator identifier>& 
          errorFormat=json& 
          contentKey=<your content key>& 
          iv=<your iv here>"
     ```

     ライセンストークン URL の応答は次のようになります。

     ```
     https://fp.service.expressplay.com:80/hms/fp/rights/? 
          ExpressPlayToken=<base64-encoded ExpressPlay token>
     ```

1. ExpressPlay のライセンストークン URL を持つ変数を設定します。

   例：

   ```js
   var myServerProcessSPCPath = 'https://fp.service.expressplay.com:80/hms/fp/rights/? 
        ExpressPlayToken=<base64-encoded ExpressPlay token>';
   ```

1. アプリで保護されたコンテンツを再生する前に、次の場所からコンテンツの URL スキームを変更します。 `skd://` から `https://`.

   再生を許可するライセンスサーバーを呼び出す前に、アプリにこの URL スキームを追加する必要があります。

   プロトコルを変更する必要があるのは、鍵管理システムのコンテンツキーへのアクセスを提供するコンテンツ ID が、M3U8 マニフェスト内で `skd://` プロトコルを使用します。 保護されたコンテンツを再生するためのライセンスを取得する準備が整ったら、まずプロトコルを切り替えて、ExpressPlay ライセンスサーバーと通信する必要があります。 次の例では、 `myServerProcessSPCPath` は、ライセンスサーバー要求の正しい URL スキームを含むように変更されます。

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
