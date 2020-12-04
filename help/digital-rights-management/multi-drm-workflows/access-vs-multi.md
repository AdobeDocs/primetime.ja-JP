---
description: AdobeのPrimetime Access DRMソリューションに詳しい方は、AccessとPrimetime Cloud DRM（ExpressPlayソリューションを利用）の間に、基本的なアーキテクチャの違いがいくつかあります。
seo-description: AdobeのPrimetime Access DRMソリューションに詳しい方は、AccessとPrimetime Cloud DRM（ExpressPlayソリューションを利用）の間に、基本的なアーキテクチャの違いがいくつかあります。
seo-title: AccessからMulti-DRMへの移行
title: AccessからMulti-DRMへの移行
uuid: 3e33ca9a-867e-46b8-bf88-8dbfe14ff786
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# AccessからMulti-DRMへの移行{#migrating-from-access-to-multi-drm}

AdobeのPrimetime Access DRMソリューションに詳しい方は、AccessとPrimetime Cloud DRM（ExpressPlayソリューションを利用）の間に、基本的なアーキテクチャの違いがいくつかあります。

## AccessとMulti-DRMのアーキテクチャの違い

|  | アクセス | Multi-DRM |
|---|---|---|
| **パッケージ** | Packagerがライセンスサーバーにバインドされています。 コンテンツをパッケージ化する際、Packagerはライセンスサーバーの公開鍵を知っている必要があります。 | Packagerが1つのライセンスサーバーに結び付けられていません。 |
|  | コンテンツをパッケージ化すると、そのコンテンツは特定のライセンスサーバーに結び付けられます。 | コンテンツが特定のライセンスサーバーに結び付けられるわけではありません。 この方法の効果の1つは、実稼働用ライセンスを取得する前にすべてのコンテンツをパッケージ化できることです。 |
|  | キーは暗号化された後に（メタデータとして）コンテンツ自体に安全に埋め込まれるので、Packagerがキーストレージと通信する必要はありません。 読み取れるのは、対応するライセンスサーバーだけです。 | キーは、キーストレージシステムから&#x200B;*Packagerに*&#x200B;送信するか、*Packagerから* Packagerをキーストレージシステムに送信する必要があります。 キーストレージシステムは、お客様独自のシステムか、ExpressPlayのKeyストレージのいずれかです。 |
| **権利付与** | クライアントがAccess Cloudサービスにコンテンツをリクエストします。 次に、Accessクラウドサービスが、ユーザーの権利付与システムにリクエストを行います。 ユーザーの権利付与システムは、ユーザーの権利付与を返します。 （クライアントは、ライセンスリクエストを行う前に、お客様のサーバーからログイン用のcookieを取得している可能性があります）。 | クライアントが顧客のストアフロントにトークンをリクエストします（これは、以前に顧客が認証cookieを取得していたのと同じワークフローの場合があります）。 この時点で、ユーザーが権限チェックを実行します。 権限チェックに合格した場合は、そのユーザー用のトークンを生成するリクエストをExpressPlayサーバーに送信します。 このトークンは常に特定のコンテンツに結び付けられ、*は特定のデバイスに結び付けられます。* 顧客のストアフロントは、トークンをクライアントに返します。 クライアントがDRM再生リクエストを行うと、トークンはリクエストに含まれ、ExpressPlayのDRMサーバーは顧客のサーバーに呼び出さずにトークンを検証します。 |