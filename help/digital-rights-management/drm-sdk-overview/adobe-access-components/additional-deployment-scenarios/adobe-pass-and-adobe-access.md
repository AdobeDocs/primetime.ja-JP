---
title: Adobe Primetime認証とAdobe PrimetimeDRM
description: Adobe Primetime認証とAdobe PrimetimeDRM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Adobe Primetime認証とAdobe PrimetimeDRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

Adobe Primetime認証([https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/))は、複数のコンテンツプロバイダーでユーザー/デバイスの認証と承認を行います。 有効なケーブルテレビまたは衛星テレビ購読が必要です。

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Primetime認証は、AdobePrimetime DRMと共に使用して、メディアコンテンツを保護できます。 このシナリオでは、ビデオプレーヤー(SWF)は、Adobe Systemsがホストする&#x200B;*アクセスイネーブラ*&#x200B;と呼ばれる別のSWFを読み込むことができます。 *Access Enabler*&#x200B;は、Adobe Primetime認証サービスに接続し、MVPD（マルチチャネルビデオプログラミングディストリビュータ）IDプロバイダシステムとのSAML SSO統合を容易にするために使用されます。 これには、ユーザーのブラウザーを短時間MVPDログインページにリダイレクトし、AuthNトークンを保存して、最後にキャッシュされたAuthNセッションを使用してコンテンツWebサイトに戻ることが関係します。

*Access Enabler*&#x200B;は、Adobe Primetime認証サービスとMVPDとの間のバックエンド認証を容易にします。 MVPDはビジネスロジックを維持し、ユーザーが権利を持つコンテンツを決定します。 エンタイトルメントは、そのコンテンツリソースの追加のAuthZトークンに保持され、クライアントに送り返されます。

認証および認証トークンは、Primetime DRMクライアントの一意のIDと秘密鍵を使用して署名され、改ざんやスプーフィングを避けます。 このトークンは、*アクセスイネーブラ*&#x200B;を介してのみアクセスできます。

ビデオプレーヤーは、*アクセスイネーブラ*&#x200B;で`getAuthorization`を呼び出すことで、プロセスをトリガーできます。 有効なAuthN/AuthZトークンが存在する場合、*AccessEnabler*&#x200B;は、ビデオコンテンツを再生するための短時間のみ有効なメディアトークンを含むビデオプレーヤーへのコールバックを発行します。

Adobe Primetime認証は、サーバーにデプロイできるメディアトークンバリデーターJavaライブラリを提供します。 コンテンツ保護にPrimetime DRMサーバーを使用する場合、メディアトークンバリデーターをPrimetime DRMサーバーサイドプラグインと統合し、メディアトークンの検証が成功した後に汎用ライセンスを自動的に発行できます。 次に、コンテンツがCDNサーバーからクライアントにストリーミングされます。 コンテンツのライセンスを取得するには、短時間のみ有効なメディアトークンをPrimetime DRMサーバーに送信し、そこでトークンの有効性を検証し、ライセンスを発行します。

長期間有効なAuthNトークンは、通常、MVPD加入者のAuthNを表すために、すべてのコンテンツ開発者の&#x200B;*Access Enabler*&#x200B;で使用されます。 また、Primetime DRMサーバーとトークン検証ツールは、コンテンツプロバイダーに代わってCDNまたはサービスプロバイダーーで操作できます。