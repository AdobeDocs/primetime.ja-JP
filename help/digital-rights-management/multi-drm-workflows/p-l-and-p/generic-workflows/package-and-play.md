---
description: ExpressPlay の Bento4 パッケージャーを使用して、ExpressPlay を利用した Primetime Cloud DRM でサポートされる DRM ソリューションのコンテンツを準備できます。
title: ExpressPlay Packager / Cloud DRM / TVSDK
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ExpressPlay Packager / Cloud DRM / TVSDK {#expressplay-packager-cloud-drm-tvsdk}

ExpressPlay の Bento4 パッケージャーを使用して、ExpressPlay を利用した Primetime Cloud DRM でサポートされる DRM ソリューションのコンテンツを準備できます。

このタスクでは、サードパーティツールを使用して保護されたコンテンツを準備する方法について説明します。 *ExpressPlay Bento4 ツール*：様々な DRM ソリューションで使用します。 詳しくは、 *Bento4 ツール* に関するドキュメント [ExpressPlay](https://www.expressplay.com/developer/) Web サイト。
1. ExpressPlay アカウントを取得し、ExpressPlay のユーザー認証子情報を取得します。

   詳しくは、 [Primetime DRM Cloud のクイックスタート。](../../quick-start/quick-overview.md)
1. Primetime Access 用にコンテンツを暗号化する場合は、PrimetimeAdobeアクセス SDK と必要な証明書（ライセンス、トランスポートおよびパッケージング証明書）をAdobeから取得します。
1. DRM システムで使用するコンテンツ暗号化キー (CEK) とコンテンツ暗号化キーストレージ ID(CEKSID) を指定します。 （OpenSSL などを使用してランダムに生成します）。

   CEK は、ビデオファイルの暗号化に使用する実際のキーです。 独自の鍵管理システム内の独自のサーバーに安全に保管するか、ExpressPlay の [主要ストレージソリューション](https://www.expressplay.com/developer/key-storage/).

   CEKSID は、特定の CEK の識別子です。 （通常）暗号化キーを渡さない。 例えば、ライセンストークンを要求する際には、CEKSID を指定します。

1. Access 用にコンテンツを暗号化する場合は、CEK を利用して、コンテンツに関連付けられた Primetime Access メタデータを作成します。

1. コンテンツをフラグメント化して、 *Bento4 MP4DASH* ツールを使用します。

   この手順では、 *MP4FRAGMENT* ツールを使用します。 コンテンツのフラグメント化は 1 回だけ実行する必要があります。 例：

   ```
   ./mp4fragment Unfragmented.mp4 Fragmented.mp4
   ```

1. 以下を使用します。 *Bento4 MPDASH* ツールを使用して、断片化されたコンテンツを「DASH 化」および暗号化します。

   使用するすべての DRM システムを指定し、前の手順で生成された Primetime Access メタデータを渡すには、このコマンドを使用します。 例：

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
   
   1. コンテンツの顧客選択。 この実装では、クライアントが特定のコンテンツ ID のコンテンツトークンをリクエストするために、エンドポイントを含める必要があります。
   1. 顧客の権利付与
   1. クライアントからのライセンストークン (ExpressPlay) リクエスト ( [ExpressPlay ライセンストークンリクエスト/レスポンスのリファレンス](../../license-token-req-resp-ref/license-req-resp-overview.md))

1. クライアントを作成します。

   クライアントにはストアフロントサーバーへの呼び出しを含める必要があります。 Adobeでは、ユーザーがコンテンツを選択した後、およびユーザーが認証された後に、クライアントがストアフロントを呼び出すことをお勧めします。 次に、ExpressPlay から返されたトークンをプレーヤーに渡し、ライセンスリクエストに使用します。 プレーヤーの DRM コンポーネントの実装の概要は、次のとおりです。

   * Browser TVSDK for Browser5HTML
   * [iOS](../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-apple-fairplay-tvsdk.md)

1. ライセンストークンを手元に置くと、クライアントはトークンからリクエスト URL を派生させ、ExpressPlay へのライセンスリクエストを作成して、選択された保護されたコンテンツをユーザー向けに再生できます。
