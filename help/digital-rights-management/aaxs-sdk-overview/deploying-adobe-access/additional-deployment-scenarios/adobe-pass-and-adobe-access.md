---
seo-title: Adobe PassとAdobe Access
title: Adobe PassとAdobe Access
uuid: 09e75cd7-00b3-4f0f-869e-43dc4d5c3bf7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Adobe PassとAdobe Access {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/))は、複数のコンテンツプロバイダー間でのユーザー/デバイスの認証と承認を提供します。 ユーザーは、有効なケーブルテレビまたは衛星テレビの購読を持っている必要があります。

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Passは、Adobe Accessと共に使用して、メディアコンテンツを保護できます。 このシナリオでは、ビデオプレーヤー(SWF)は、Adobe Systemsがホストする *Access Enabler*(Access Enabler)と呼ばれる別のSWFを読み込むことができます。 *Access Enablerは* 、Adobe Passサービスに接続し、MVPD(Multichannel Video Programming Distributor)IDプロバイダーシステムとのSAML SSO統合を容易にするために使用されます。 これには、ユーザーのブラウザーを短時間MVPDログインページにリダイレクトし、AuthNトークンを保存して、最後にAuthNキャッシュセッションを使用してコンテンツWebサイトに戻ります。

その後、 *Access Enablerを使用して* 、Adobe PassサービスとMVPDとの間のバックエンド認証を容易に行うことができます。 MVPDはビジネスロジックを維持し、ユーザーに権利を付与するコンテンツを決定します。 エンタイトルメントは、そのコンテンツリソースの追加のAuthZトークンで保持され、クライアントに送り返されます。

認証トークンと認証トークンは、改ざんやスプーフィングを避けるために、Adobe Accessクライアントの一意のIDと秘密鍵を使用して署名されます。 このトークンは、 *Access Enablerを介してのみアクセスできます*。

ビデオ・プレイヤは、 `getAuthorization` Access Enablerでを呼び出すことで、プロセスをトリ *ガーする*&#x200B;ことができます。 有効なAuthN/AuthZトークンが存在する場合、 ** AccessEnablerは、ビデオコンテンツを再生するための短時間のみ有効なメディアトークンを含む、ビデオプレーヤーへのコールバックを発行します。

Adobe Passは、サーバーにデプロイできるメディアトークンバリデーターのJavaライブラリを提供します。 コンテンツ保護にFlass Accessサーバーを使用する場合、メディアトークンバリデーターをAdobe Accessのサーバー側プラグインと統合し、メディアトークンの検証が正常に完了した後に汎用ライセンスを自動的に発行できます。 その後、コンテンツがCDNサーバーからクライアントにストリーミングされます。 コンテンツのライセンスを取得するには、短時間のみ有効なメディアトークンをAdobe Accessサーバーに送信し、トークンの有効性を検証し、ライセンスを発行します。

長期間有効なAuthNトークンは、通常、すべてのコンテンツ開発者の *Access* Enablerで使用され、そのMVPD加入者のAuthNを表します。 また、Adobe Access ServerとToken Verifierは、CDNまたはサービスプロバイダーがコンテンツプロバイダーに代わって操作できます。
