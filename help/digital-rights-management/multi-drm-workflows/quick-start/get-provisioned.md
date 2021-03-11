---
description: Primetime DRM Cloudを使用し始めるには、ExpressPlayを利用します。Adobeの担当者の支援を得て、Adobe証明書およびExpressPlayアカウントを設定する必要があります。
title: プロビジョニング（アカウントなど）
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# プロビジョニング（アカウントなど） {#get-provisioned-accounts-etc}

Primetime DRM Cloudを使用し始めるには、ExpressPlayを利用します。Adobeの担当者の支援を得て、Adobe証明書およびExpressPlayアカウントを設定する必要があります。

1. Adobeの担当者に問い合わせて、TVSDKでMulti-DRMを実装するのに必要なAdobe証明書およびExpressPlayアカウントをリクエストします。

       連絡先として使用する電子メールアドレスをAdobeの担当者に伝えます。Adobeが次の2つのアカウントを作成します：
   
   * ***証明書ポータルアカウント*** - ( <span></span>https://certportal.primetime.adobe.com):Access / Primetime DRM *Adobe証明書登録管理* チームは、指定したアドレスに電子メールを送信します。電子メールには、Adobe証明書ポータルのURLと、Adobeの証明書登録ドキュメントへのリンクが含まれています(最新のドキュメントはこちらを参照してください：[証明書登録ガイド](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md))。

   * ***ExpressPlayアカウント*** -Adobeから、ExpressPlay管理者アカウントの登録に使用するリンクを含む電子メールが送信されます。

1. Adobe IDを使用してAdobe証明書ポータルにログインします(Adobeの担当者に入力したのと同じ電子メールアドレスを使用します)。 まだAdobe IDをお持ちでない場合は、証明書ポータルの&#x200B;*Adobe ID*&#x200B;リンクを使ってすばやく作成できます。

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Adobe証明書ポータルで、*体験版*&#x200B;証明書を要求します。

   体験版Multi-DRMの場合、1つの体験版用証明書でコンテンツ保護の次のすべての側面をカバーします。パッケージ、ライセンス、およびトランスポート。 証明書を要求するには、独自の[CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md)を指定する必要があります。
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobeから、証明書要求の受け入れまたは拒否を示す電子メールが送信されます。 証明書要求のステータスは、証明書ポータルの&#x200B;*「Request history*」タブで確認できます。
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. ExpressPlay管理者アカウントを作成します。

   Adobeから提供されたExpressPlayへのリンクに従います。 ExpressPlayに&#x200B;*アカウントを作成*&#x200B;ページが開きます。 必要な情報を入力し、フォームを送信します。 1週間有効なアクティベーションリンクを含む電子メールを`operations@expressplay.com`から受信します。 アクティベート後、ExpressPlayサービスを設定します。
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   サービスを作成すると、独自の管理ページが表示されます。 一部のアクティビティ追跡フィールドと共に、本番用とテスト用の&#x200B;*ユーザー認証子* （APIキー）、本番用とテスト用のサービスURLが表示されます。

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. FairPlayを使用している場合は、ExpressPlayを設定するための追加手順が（Appleの開発者サイトで）必要です。 手順については、[FairPlay用のExpressPlayサービスを有効にする](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay)を参照してください。
