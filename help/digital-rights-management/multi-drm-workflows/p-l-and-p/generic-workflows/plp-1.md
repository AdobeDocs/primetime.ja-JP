---
description: アドビのオフラインパッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。
seo-description: アドビのオフラインパッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。
seo-title: Primetime Packager/Cloud DRM/TVSDK
title: Primetime Packager/Cloud DRM/TVSDK
uuid: e54a0e4d-c8ea-46d4-b1b0-bed8a680f8f5
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Primetime Packager/Cloud DRM/TVSDK {#primetime-packager-cloud-drm-tvsdk}

アドビのオフラインパッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。

この一連の手順は、ExpressPlayの管理者アカウントが既に設定済みであることを前提としています。Primetime DRM [Cloudのクイックスタート](../../../multi-drm-workflows/quick-start/quick-overview.md)。
1. コンテンツのパッケージ化に使用するインフラストラクチャを選択します。 Primetime Packagerは、FairPlay、WidevineおよびPlayReady DRMで使用するコンテンツのパッケージ化を、コマンドラインおよび設定ベースでサポートしています。 TVSDKでは、現在、次の形式と暗号化がサポートされています（今後、より多くの形式が導入されます）。

   * DASH(CENC)/PlayReady、Widevine - HTML5用
   * HLS/FairPlay、アクセス — iOS用

1. キー管理システム(KMS)を選択します。

   * ExpressPlayのKMS( [ExpressPlay Key Storage](https://www.expressplay.com/developer/key-storage/))を使用このシステムは、ExpressPlayのRESTful APIを使用してコンテンツキーを管理します。

      または…

   * 独自のKMSを設定します。 コンテンツキーのデータベースを作成し、コンテンツIDで選択可能にします。

      どちらの場合も、KMSは提供されるコンテンツキーを管理し、各キーにはコンテンツIDが関連付けられています。

1. コンテンツをパッケージ化します。 Primetime Packagerを使用すると、特定のDRMソリューションまたは複数のDRMソリューション用にコンテンツの一部をパッケージ化できます。

   次のサンプルコマンドは、様々なDRMソリューション用にコンテンツをパッケージ化する例を示しています。

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
      >この値 `key_url` は、M3U8ファイル内と同様にコピーされます。

1. 「ストアフロントサーバー」を作成します。

       ストアフロントサーバーは、次の操作を処理する必要があります。
   
   1. コンテンツの顧客選択。 この実装には、特定のコンテンツIDのコンテンツトークンをリクエストするクライアントのエンドポイントを含める必要があります。
   1. 顧客の権利付与
   1. クライアントからのライセンストークン(ExpressPlay)リクエスト( [ExpressPlayライセンストークンリクエスト/レスポンスリファレンス](../../../multi-drm-workflows/license-token-req-resp-ref/license-req-resp-overview.md))

1. クライアントを作成します。

       クライアントにはストアフロントサーバーへの呼び出しが含まれている必要があります。 ユーザーがコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことをお勧めします。 次に、ExpressPlayから返されたトークンをプレーヤーに渡し、ライセンスリクエストに使用します。 プレーヤーのDRMコンポーネントの実装の概要を以下に示します。
   
   * [HTML5のブラウザーTVSDK](https://help.adobe.com/en_US/primetime/psdk/browser_tvsdk/index.html#PSDKs-reference-DRM_interface_overview)
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを入手したクライアントは、トークンからリクエストURLを取得し、ExpressPlayにライセンスリクエストを作成し、選択したコンテンツを再生できるようになりました。
