---
description: Adobeのオフラインパッケージャーを使用して、ExpressPlay を利用した Primetime Cloud DRM でサポートされる DRM ソリューション用のコンテンツを準備できます。
title: Primetime Packager/Cloud DRM/TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Primetime Packager/Cloud DRM/TVSDK {#primetime-packager-cloud-drm-tvsdk}

Adobeのオフラインパッケージャーを使用して、ExpressPlay を利用した Primetime Cloud DRM でサポートされる DRM ソリューション用のコンテンツを準備できます。

この一連の手順は、ExpressPlay の管理者アカウントが既に設定されていることを前提としています。 [Primetime DRM クラウドのクイックスタート](../../../multi-drm-workflows/quick-start/quick-overview.md).
1. コンテンツのパッケージ化に使用するインフラストラクチャを選択します。 Primetime Packager は、FairPlay、Widevine、PlayReady DRM で使用するコンテンツのコマンドラインと設定ベースのパッケージを両方ともサポートしています。 現在、TVSDK では次の形式と暗号化がサポートされています（パイプライン内でさらに多くの形式がサポートされています）。

   * DASH(CENC)/PlayReady、Widevine -HTML5 用
   * HLS / FairPlay、アクセス — iOS向け

1. キー管理システム (KMS) を選択してください：

   * ExpressPlay の KMS ( [ExpressPlay キーストレージ](https://www.expressplay.com/developer/key-storage/))；このシステムは、ExpressPlay の RESTful API を介してコンテンツキーを管理します。

     または…

   * 独自の KMS を設定します。 コンテンツキーのデータベースを作成し、コンテンツ ID で選択可能にします。

     どちらの場合も、KMS はコンテンツキーの提供を管理し、各キーには Content-ID が関連付けられています。

1. コンテンツをパッケージ化します。 Primetime Packager を使用すると、特定の DRM ソリューションまたは複数の DRM ソリューション用にコンテンツをパッケージ化できます。

   次のサンプルコマンドは、様々な DRM ソリューション用にコンテンツをパッケージ化する例を示しています。

   * [Widevine with Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19) （MPD ファイルを生成）:

     ```
     java -jar OfflinePackager.jar \ 
       -in_path [ 
       <your_content.mp4>] \ 
       -out_type dash \ 
       -out_path [ 
       <your_out_file_path>] \ 
       -drm \ 
       -drm_sys WIDEVINE \ 
       -key_file_path "creds/widevine_key.bin" \ 
       -widevine_key_id [ 
       <some_keyID>] \ 
       -widevine_content_id [ 
       <some_content-ID] \ 
       -widevine_header provider:intertrust#content_id:2a
     ```

   * [FairPlay with Primetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20) （M3U8 ファイルを生成）:

     ```
     java -jar OfflinePackager.jar  
       -in_path [ 
       <your_content.mp4>]  
       -out_type hls  
       -out_path [ 
       <your_out_file_path>]  
       -drm  
       -drm_sys FAIRPLAY  
       -key_file_path "creds/fairplay_key.bin"  
       -key_url "user_provided_value"
     ```

     >[!NOTE]
     >
     >The `key_url` の値は、M3U8 ファイル内と同様にコピーされます。

1. 「ストアフロントサーバー」を作成します。

       ストアフロントサーバーは、次の操作を処理する必要があります。
   
   1. コンテンツの顧客選択。 この実装では、クライアントが特定のコンテンツ ID のコンテンツトークンをリクエストするために、エンドポイントを含める必要があります。
   1. 顧客の権利付与
   1. クライアントからのライセンストークン (ExpressPlay) リクエスト ( [ExpressPlay ライセンストークンリクエスト/レスポンスのリファレンス](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. クライアントを作成します。

       クライアントにはストアフロントサーバーへの呼び出しを含める必要があります。 Adobeでは、ユーザーがコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことをお勧めします。 次に、ExpressPlay から返されたトークンをプレーヤーに渡し、ライセンスリクエストに使用します。 プレーヤーの DRM コンポーネントの実装の概要は、次のとおりです。
   
   * [Browser TVSDK for Browser5HTML](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを手元に置いた状態で、クライアントはトークンからリクエスト URL を派生させ、ExpressPlay へのライセンスリクエストを作成してから、ユーザーに対して選択したコンテンツを再生できます。
