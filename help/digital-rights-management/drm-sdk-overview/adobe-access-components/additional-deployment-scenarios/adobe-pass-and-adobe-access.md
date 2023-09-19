---
title: Adobe Primetime認証とAdobe Primetime DRM
description: Adobe Primetime認証とAdobe Primetime DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# Adobe Primetime認証とAdobe Primetime DRM {#adobe-primetime-authentication-and-adobe-primetime-drm}

Adobe Primetime認証 ( [https://www.adobe.com/products/adobepass/](https://www.adobe.com/products/adobepass/)) は、複数のコンテンツプロバイダーに対してユーザー/デバイスの認証と承認をおこないます。 ユーザーは、有効なケーブル TV または衛星 TV のサブスクリプションを持っている必要があります。

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Primetime認証は、メディアコンテンツを保護するためにAdobePrimetime DRM と共に使用できます。 このシナリオでは、ビデオプレーヤー (SWF) は、 *Access Enabler*:Adobe Systemsがホストします。 The *Access Enabler* は、Adobe Primetime認証サービスに接続し、MVPD(Multichannel Video Programming Distributor) の id プロバイダーシステムとの SAML SSO 統合を容易にするために使用されます。 これには、ユーザーのブラウザーを MVPD ログインページに短時間リダイレクトし、AuthN トークンを保持してから、キャッシュされた AuthN セッションを使用してコンテンツ Web サイトに戻る必要があります。

The *Access Enabler* これにより、Adobe Primetime認証サービスと MVPD 間のバックエンド認証を容易におこなうことができます。 MVPD は、ビジネスロジックを維持し、ユーザーが使用できるコンテンツを決定します。 使用権限は、そのコンテンツリソースの追加の AuthZ トークンで保持され、クライアントに返されます。

認証および承認トークンは、改ざんやスプーフィングを避けるために、Primetime DRM クライアントの一意の ID と秘密鍵を使用して署名されます。 このトークンには、 *Access Enabler*.

ビデオプレーヤーは、 `getAuthorization` の *Access Enabler*. 有効な AuthN/AuthZ トークンが存在する場合、 *AccessEnabler* は、ビデオコンテンツを再生するための短時間のみ有効なメディアトークンを含む、ビデオプレーヤーへのコールバックを発行します。

Adobe Primetime認証は、サーバーにデプロイできるメディアトークンバリデーター Java ライブラリを提供します。 コンテンツ保護に Primetime DRM サーバーを使用する場合、メディアトークンバリデーターを Primetime DRM サーバー側プラグインと統合して、メディアトークンの検証が成功した後に汎用ライセンスを自動的に発行できます。 その後、コンテンツが CDN サーバーからクライアントにストリーミングされます。 コンテンツライセンスを取得するには、短時間のみ有効なメディアトークンを Primetime DRM サーバーに送信し、そのサーバーでトークンの有効性を検証し、ライセンスを発行します。

長期間有効な AuthN トークンは、通常、 *Access Enabler* をまたいで、その MVPD サブスクライバーの AuthN を表すすべてのコンテンツ開発者。 さらに、Primetime DRM サーバーとトークン検証ツールは、CDN またはサービスプロバイダーがコンテンツプロバイダーに代わって操作できます。
