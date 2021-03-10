---
title: Adobe PassとAdobeへのアクセス
description: Adobe PassとAdobeへのアクセス
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Adobe PassとAdobeへのアクセス{#adobe-pass-and-adobe-access}

Adobe Pass([](https://www.adobe.com/products/adobepass/))は、複数のコンテンツプロバイダーでユーザー/デバイスの認証と承認を行います。 有効なケーブルテレビまたは衛星テレビ購読が必要です。

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Passは、Adobeアクセスと併用してメディアコンテンツを保護できます。 このシナリオでは、ビデオプレーヤー(SWF)は、Adobe Systemsがホストする&#x200B;*アクセスイネーブラ*&#x200B;と呼ばれる別のSWFを読み込むことができます。 *Access Enabler*&#x200B;は、Adobe Passサービスに接続し、MVPD（マルチチャネルビデオプログラミングディストリビュータ）IDプロバイダシステムとのSAML SSO統合を容易にするために使用されます。 これには、ユーザーのブラウザーを短時間MVPDログインページにリダイレクトし、AuthNトークンを保存して、最後にキャッシュされたAuthNセッションを使用してコンテンツWebサイトに戻ることが関係します。

*Access Enabler*&#x200B;は、Adobe PassサービスとMVPDとの間のバックエンド認証を容易にします。 MVPDはビジネスロジックを維持し、ユーザーが権利を持つコンテンツを決定します。 エンタイトルメントは、そのコンテンツリソースの追加のAuthZトークンに保持され、クライアントに送り返されます。

認証および認証トークンは、Adobeアクセスクライアントの一意のIDと秘密キーを使用して署名され、改ざんやスプーフィングを防ぎます。 このトークンは、*アクセスイネーブラ*&#x200B;を介してのみアクセスできます。

ビデオプレーヤーは、*アクセスイネーブラ*&#x200B;で`getAuthorization`を呼び出すことで、プロセスをトリガーできます。 有効なAuthN/AuthZトークンが存在する場合、*AccessEnabler*&#x200B;は、ビデオコンテンツを再生するための短時間のみ有効なメディアトークンを含むビデオプレーヤーへのコールバックを発行します。

Adobe Passは、サーバーにデプロイできるメディアトークンバリデーターJavaライブラリを提供しています。 コンテンツ保護にFlass Accessサーバーを使用する場合、メディアトークンバリデーターをAdobeアクセスサーバー側プラグインと統合して、メディアトークンの検証が正常に完了した後に汎用ライセンスを自動的に発行できます。 次に、コンテンツがCDNサーバーからクライアントにストリーミングされます。 コンテンツのライセンスを取得するには、短時間のみ有効なメディアトークンをAdobeアクセスサーバに送信し、そのサーバでトークンの有効性を検証し、ライセンスを発行します。

長期間有効なAuthNトークンは、通常、MVPD加入者のAuthNを表すために、すべてのコンテンツ開発者の&#x200B;*Access Enabler*&#x200B;で使用されます。 また、Adobe Access Serverとトークンの検証は、CDNまたはサービスプロバイダーがコンテンツプロバイダーに代わって操作できます。
