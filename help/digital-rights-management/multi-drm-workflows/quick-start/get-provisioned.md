---
description: Primetime DRM CloudをExpressPlayで利用できるようにするには、アドビの担当者の支援を得て、Adobe証明書およびExpressPlayアカウントを設定する必要があります。
seo-description: Primetime DRM CloudをExpressPlayで利用できるようにするには、アドビの担当者の支援を得て、Adobe証明書およびExpressPlayアカウントを設定する必要があります。
seo-title: プロビジョニングの実施（アカウントなど）
title: プロビジョニングの実施（アカウントなど）
uuid: 51b95676-2121-4d8b-8756-9fd097185a13
translation-type: tm+mt
source-git-commit: 9792aff8586c46aabb5bfb70864cfe98c28e602d

---


# プロビジョニングの実施（アカウントなど） {#get-provisioned-accounts-etc}

Primetime DRM CloudをExpressPlayで利用できるようにするには、アドビの担当者の支援を得て、Adobe証明書およびExpressPlayアカウントを設定する必要があります。

1. アドビの担当者に連絡し、TVSDKでMulti-DRMを実装するために必要なAdobe証明書およびExpressPlayアカウントをリクエストします。

       お客様の連絡先として使用する電子メールアドレスをアドビの担当者に伝えます。 次に、アドビが2つのアカウントを作成します。
   
   * ***証明書ポータルアカウント*** - (<span></span>https://certportal.primetime.adobe.com) :Adobe Access / Primetime DRM *証明書登録管理チームは* 、指定したアドレスに電子メールを送信します。 この電子メールには、Adobe証明書ポータルのURLと、アドビの証明書登録ドキュメントへのリンクが含まれています（最新のドキュメントは次のURLにあります）。証明 [書登録ガイド](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md))。

   * ***ExpressPlayアカウント*** - ExpressPlay管理者アカウントの登録に使用するリンクを含む電子メールがアドビから送信されます。

1. Adobe IDを使用してAdobe証明書ポータルにログインします（アドビの担当者に入力したのと同じ電子メールアドレスを使用します）。 まだAdobe IDをお持ちでない場合は、証明書ポータルの「 *Get an Adobe ID* 」リンクに従って、すばやく作成できます。

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Adobe証明書ポータルで、体験版証明書を *要求します* 。

   Multi-DRM体験版の場合、1つの体験版証明書でコンテンツ保護の次の側面をすべてカバーします。パッケージ化、ライセンス、およびトランスポート。 証明書を要求するには、独自の [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) ：を指定する必要があります。
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   証明書リクエストの承認または拒否を示す電子メールがアドビから送信されます。 証明書要求のステータスは、証明書ポータルの「 *Request history* 」タブで確認できます。
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. ExpressPlay管理者アカウントを作成します。

   アドビから提供されたExpressPlayへのリンクに従います。 ExpressPlayで「アカウ *ントを作成* 」ページが開きます。 必要な情報を入力し、フォームを送信します。 1週間有効なライセンス認証リ `operations@expressplay.com` ンクを含む電子メールが届きます。 アクティブ化した後、ExpressPlayサービスを設定します。
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   サービスを作成すると、独自の管理ページが表示されます。 一部のアクティビティ追跡フィールドに加えて、実稼動およびテストの *顧客認証子* （APIキー）、実稼動およびテストのサービスURLが表示されます。

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. FairPlayを使用している場合は、ExpressPlayを設定するための追加の手順が（Appleの開発者サイトで）必要です。 手順につ [いては、FairPlay向けExpressPlayサービスの有効化](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) （英語のみ）を参照してください。
