---
seo-title: Adobe Primetime認証とAdobe Primetime DRM
title: Adobe Primetime認証とAdobe Primetime DRM
uuid: 44fe3956-efb5-4fc5-97e2-37abb6554322
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime認証とAdobe Primetime DRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

Adobe Primetime認証(https://www.adobe.com/products/adobepass/ [](https://www.adobe.com/products/adobepass/))は、複数のコンテンツプロバイダー間でのユーザー/デバイスの認証と認証を提供します。 ユーザーは、有効なケーブルテレビまたは衛星テレビの購読を持っている必要があります。

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Primetime認証は、Adobe Primetime DRMと共に使用して、メディアコンテンツを保護できます。 このシナリオでは、ビデオプレーヤー(SWF)は、Adobe Systemsがホストする *Access Enabler*(Access Enabler)と呼ばれる別のSWFを読み込むことができます。 *Access Enablerは* 、Adobe Primetime認証サービスに接続し、MVPD（マルチチャネルビデオプログラミングディストリビュータ）IDプロバイダーシステムとのSAML SSOの統合を容易にするために使用されます。 これには、ユーザーのブラウザーを短時間MVPDログインページにリダイレクトし、AuthNトークンを保存して、最後にAuthNキャッシュセッションを使用してコンテンツWebサイトに戻ります。

その後 *、Adobe Primetime認証サービスと* MVPDの間のバックエンド認証を容易に行うことができます。 MVPDはビジネスロジックを維持し、ユーザーに権利を付与するコンテンツを決定します。 エンタイトルメントは、そのコンテンツリソースの追加のAuthZトークンで保持され、クライアントに送り返されます。

認証トークンと認証トークンは、改ざんやスプーフィングを避けるために、Primetime DRMクライアントの一意のIDと秘密鍵を使用して署名されます。 このトークンは、 *Access Enablerを介してのみアクセスできます*。

ビデオ・プレイヤは、 `getAuthorization` Access Enablerでを呼び出すことで、プロセスをトリ *ガーする*&#x200B;ことができます。 有効なAuthN/AuthZトークンが存在する場合、 ** AccessEnablerは、ビデオコンテンツを再生するための短時間のみ有効なメディアトークンを含む、ビデオプレーヤーへのコールバックを発行します。

Adobe Primetime認証は、サーバーにデプロイできるメディアトークンバリデーターのJavaライブラリを提供します。 コンテンツ保護にPrimetime DRMサーバーを使用する場合、メディアトークンバリデーターをPrimetime DRMサーバー側プラグインと統合して、メディアトークンの検証が正常に完了した後に汎用ライセンスを自動的に発行できます。 その後、コンテンツがCDNサーバーからクライアントにストリーミングされます。 コンテンツのライセンスを取得するには、短時間のみ有効なメディアトークンをPrimetime DRMサーバーに送信し、トークンの有効性を検証し、ライセンスを発行します。

長期間有効なAuthNトークンは、通常、すべてのコンテンツ開発者の *Access* Enablerで使用され、そのMVPD加入者のAuthNを表します。 また、Primetime DRMサーバーとトークン検証ツールは、CDNまたはサービスプロバイダーがコンテンツプロバイダーの代わりに操作できます。