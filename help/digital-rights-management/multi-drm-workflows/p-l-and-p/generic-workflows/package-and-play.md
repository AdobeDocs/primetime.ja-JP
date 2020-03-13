---
description: ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。
seo-description: ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。
seo-title: ExpressPlay Packager/Cloud DRM/TVSDK
title: ExpressPlay Packager/Cloud DRM/TVSDK
uuid: 0d2f5a8d-15c4-42ba-acb8-1dc8d5bc62de
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ExpressPlay Packager/Cloud DRM/TVSDK {#expressplay-packager-cloud-drm-tvsdk}

ExpressPlayのBento4パッケージャーを使用して、Primetime Cloud DRM（ExpressPlayを利用）でサポートされているDRMソリューションのコンテンツを準備できます。

このタスクでは、様々なDRMソリューションで使用する、保護されたコンテンツ(この場合は *ExpressPlay Bento4ツール*)を準備するサードパーティのツールを使用する方法について説明します。 詳しくは、ExpressPlay Webサイトの *Bento4 tools* documentationを参照 [](https://www.expressplay.com/developer/) してください。
1. ExpressPlayアカウントを取得し、ExpressPlayのユーザー認証子情報を取得します。

   Primetime DRM Cloudのク [イックスタートを参照してください。](../../quick-start/quick-overview.md)
1. Primetime Access用にコンテンツを暗号化する場合は、必要な証明書（ライセンス、トランスポート、パッケージ化の証明書）と共に、Primetime Adobe Access SDKをアドビから入手します。
1. DRMシステムで使用するコンテンツ暗号化キー(CEK)とコンテンツ暗号化キーストレージID(CEKSID)を指定します。 （OpenSSLなどを使用して、ランダムに生成します）。

   CEKは、ビデオファイルの暗号化に使用する実際のキーです。 独自の鍵管理システム内の独自のサーバに安全に保存するか、ExpressPlayの鍵保存ソリューションを利用す [ることができます](https://www.expressplay.com/developer/key-storage/)。

   CEKSIDは、特定のCEKの識別子です。 （通常は）暗号化キーを渡しません。 例えば、ライセンストークンをリクエストする場合は、CEKSIDを指定します。

1. Access用にコンテンツを暗号化する場合は、CEKを利用して、コンテンツに関連付けられたPrimetime Accessメタデータを作成します。

1. コンテンツをフラグメント化して、 *Bento4 MP4DASHツール用に準備します* 。

   この手順では、 *MP4FRAGMENTツールを使用できます* 。 コンテンツをフラグメント化する必要があるのは1回だけです。 例：

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. Bento4 MPDASH ** ツールを使用して、フラグメント化されたコンテンツを「DASH化」し、暗号化します。

   このコマンドを使用して、利用するすべてのDRMシステムを指定し、前の手順で生成されたPrimetime Accessメタデータを渡します。 例：

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

       このサーバーは、次の操作を処理する必要があります。
   
   1. コンテンツの顧客選択。 この実装には、特定のコンテンツIDのコンテンツトークンをリクエストするクライアントのエンドポイントを含める必要があります。
   1. 顧客の権利付与
   1. クライアントからのライセンストークン(ExpressPlay)リクエスト( [ExpressPlayライセンストークンリクエスト/レスポンスリファレンス](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. クライアントを作成します。

   クライアントにはストアフロントサーバーへの呼び出しが含まれている必要があります。 ユーザーがコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことをお勧めします。 次に、ExpressPlayから返されたトークンをプレーヤーに渡し、ライセンスリクエストに使用します。 プレーヤーのDRMコンポーネントの実装の概要を以下に示します。

   * HTML5のブラウザーTVSDK
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを入手したクライアントは、トークンからリクエストURLを取得し、ExpressPlayにライセンスリクエストを作成し、選択した保護されたコンテンツをユーザーに対して再生できるようになりました。
