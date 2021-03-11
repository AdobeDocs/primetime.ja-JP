---
description: AdobeのOffline Packagerを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされるDRMソリューションのコンテンツを準備できます。
title: Primetime Packager/Cloud DRM/TVSDK
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Primetime Packager/Cloud DRM/TVSDK {#primetime-packager-cloud-drm-tvsdk}

AdobeのOffline Packagerを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされるDRMソリューションのコンテンツを準備できます。

この一連の説明は、ExpressPlay管理者アカウントが既に設定済みであることを前提としています。[Primetime DRM Cloudクイック開始](../../../multi-drm-workflows/quick-start/quick-overview.md)。
1. コンテンツのパッケージ化に使用するインフラストラクチャを選択します。 Primetime Packagerは、FairPlay、WidevineおよびPlayReady DRMで使用するコンテンツのパッケージ化を、コマンドラインと設定ベースの両方でサポートしています。 TVSDKでは、現在、以下の形式と暗号化がサポートされています（今後さらに多くの形式が導入されます）。

   * DASH(CENC)/PlayReady、Widevine - HTML5向け
   * HLS/FairPlay、Access - iOS向け

1. 鍵管理システム(KMS)を選択します。

   * ExpressPlayのKMSを使用([ExpressPlayキーストレージ](https://www.expressplay.com/developer/key-storage/));このシステムは、ExpressPlayのRESTful APIを使用してコンテンツキーを管理します。

      または…

   * 独自のKMSを設定します。 コンテンツキーのデータベースを作成し、コンテンツIDで選択できます。

      どちらの場合も、KMSは提供されるコンテンツキーを管理し、各キーにはコンテンツIDが関連付けられています。

1. コンテンツをパッケージ化します。 Primetime Packagerを使用すると、特定のDRMソリューションまたは複数のDRMソリューション用にコンテンツをパッケージ化できます。

   以下のサンプルコマンドは、様々なDRMソリューション用にコンテンツをパッケージ化する例を示しています。

   * [WidevineとPrimetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=19) （MPDファイルを生成）:

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

   * [FairPlayとPrimetime Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf#page=20) （M3U8ファイルを生成）:

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
      >`key_url`値は、そのままM3U8ファイルにコピーされます。

1. 「ストアフロントサーバー」を作成します。

       ストアフロントサーバーは、次の操作を処理する必要があります。
   
   1. ユーザーによるコンテンツの選択 この実装には、特定のコンテンツIDのコンテンツトークンをリクエストするクライアントのエンドポイントを含める必要があります。
   1. ユーザーの権利付与
   1. クライアントからのライセンストークン(ExpressPlay)リクエスト（[ExpressPlayライセンストークンリクエスト/レスポンスリファレンス](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md)）

1. クライアントを作成します。

       クライアントにストアフロントサーバーへの呼び出しを含める必要があります。Adobeでは、ユーザーが何らかのコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことを推奨します。 次に、ExpressPlayから返されたトークンをプレイヤーに渡して、ライセンスリクエストに使用します。 プレーヤーのDRMコンポーネントの実装については、次を参照してください：
   
   * [HTML5用のBrowser TVSDK](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを取得したクライアントは、トークンからリクエストURLを抽出し、ExpressPlayへのライセンスリクエストを作成して、選択したコンテンツを再生できるようになりました。
