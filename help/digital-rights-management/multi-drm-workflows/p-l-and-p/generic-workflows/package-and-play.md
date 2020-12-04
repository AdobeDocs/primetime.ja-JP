---
description: ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされるDRMソリューションのコンテンツを準備できます。
seo-description: ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされるDRMソリューションのコンテンツを準備できます。
seo-title: ExpressPlay Packager/Cloud DRM/TVSDK
title: ExpressPlay Packager/Cloud DRM/TVSDK
uuid: 0d2f5a8d-15c4-42ba-acb8-1dc8d5bc62de
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# ExpressPlay Packager/Cloud DRM/TVSDK {#expressplay-packager-cloud-drm-tvsdk}

ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされるDRMソリューションのコンテンツを準備できます。

このタスクでは、サードパーティのツールを使用して、様々なDRMソリューションで使用する保護されたコンテンツ（この場合は&#x200B;*ExpressPlay Bento4 Tools*）を準備する方法について説明します。 詳しくは、[ExpressPlay](https://www.expressplay.com/developer/)Webサイトの&#x200B;*Bento4 tools*&#x200B;ドキュメントを参照してください。
1. ExpressPlayアカウントを取得し、ExpressPlayのユーザー認証子情報を取得します。

   [Primetime DRMクラウドのクイック開始を参照してください。](../../quick-start/quick-overview.md)
1. Primetime Access用にコンテンツを暗号化する場合は、PrimetimeAdobeアクセスSDKと必要な証明書（ライセンス、トランスポートおよびパッケージ化の証明書）をAdobeから取得します。
1. DRMシステムで使用するコンテンツ暗号化キー(CEK)とコンテンツ暗号化キーストレージID(CEKSID)を指定します。 （OpenSSLなどを使用して、ランダムに生成します）。

   CEKは、ビデオファイルの暗号化に使用する実際のキーです。 独自の鍵管理システム内の独自のサーバーに安全に保管するか、ExpressPlayの[鍵ストレージソリューション](https://www.expressplay.com/developer/key-storage/)を利用できます。

   CEKSIDは、特定のCEKの識別子です。 （通常は）暗号化キーを渡しません。 例えば、ライセンストークンをリクエストする場合は、CEKSIDを指定します。

1. Access用にコンテンツを暗号化する場合は、CEKを利用して、コンテンツに関連付けられたPrimetime Accessメタデータを作成します。

1. コンテンツを&#x200B;*Bento4 MP4DASH*&#x200B;ツール用にフラグメント化します。

   この手順では、*MP4FRAGMENT*&#x200B;ツールを使用できます。 コンテンツのフラグメント化は1回のみ行う必要があります。 例：

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. *Bento4 MPDASH*&#x200B;ツールを使用して、「DASH化」を行い、フラグメント化されたコンテンツを暗号化します。

   使用するすべてのDRMシステムを指定し、前の手順で生成されたPrimetime Accessメタデータを渡すには、このコマンドを使用します。 例：

   ```
   /mp4dash -f  
   --use-segment-list  
   --use-segment-timeline  
   --encryption-key=<CEKSID>:<CEK>  
   --playready  
   --Widevine  
   --Widevine-header=provider:intertrust#content_id:2a  
   --primetime  
   --primetime-metadata=@AAXS.metadata 
    Fragmented.mp4 -o DASH_OUTPUT
   ```

1. 「ストアフロントサーバー」を作成します。

       このサーバーでは、次の操作を処理する必要があります。
   
   1. ユーザーによるコンテンツの選択 この実装には、特定のコンテンツIDのコンテンツトークンをリクエストするクライアントのエンドポイントを含める必要があります。
   1. ユーザーの権利付与
   1. クライアントからのライセンストークン(ExpressPlay)リクエスト（[ExpressPlayライセンストークンリクエスト/レスポンスリファレンス](../../license-token-req-resp-ref/license-req-resp-overview.md)）

1. クライアントを作成します。

   クライアントにストアフロントサーバーへの呼び出しを含める必要があります。 Adobeでは、ユーザーが何らかのコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことを推奨します。 次に、ExpressPlayから返されたトークンをプレイヤーに渡して、ライセンスリクエストに使用します。 プレーヤーのDRMコンポーネントの実装については、次を参照してください。

   * HTML5用のBrowser TVSDK
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを取得したクライアントは、トークンからリクエストURLを取得し、ExpressPlayへのライセンスリクエストを作成し、選択された保護されたコンテンツを再生できるようになりました。
