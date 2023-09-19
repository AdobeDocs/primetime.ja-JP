---
description: ExpressPlay を活用した Primetime DRM Cloud の使用を開始するには、Adobe担当者の助けを借りて、Adobe証明書および ExpressPlay アカウントを設定する必要があります。
title: プロビジョニングの依頼（アカウントなど）
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# プロビジョニングの依頼（アカウントなど） {#get-provisioned-accounts-etc}

ExpressPlay を活用した Primetime DRM Cloud の使用を開始するには、Adobe担当者の助けを借りて、Adobe証明書および ExpressPlay アカウントを設定する必要があります。

1. Adobe担当者に連絡し、TVSDK での Multi-DRM の実装に必要なAdobe証明書および ExpressPlay アカウントをリクエストします。

   連絡先として使用する E メールアドレスをAdobeの担当者に伝えます。 Adobeは、次の 2 つのアカウントを作成します。

   * ***証明書ポータルアカウント*** - ( https://certportal.primetime.adobe.com) : *Adobeアクセス/ Primetime DRM 証明書登録管理チーム* は、指定したアドレスに電子メールを送信します。 この電子メールには、Adobe証明書ポータルの URL と、Adobeの証明書登録ドキュメントへのリンクが含まれています ( 最新のドキュメントはこちらを参照してください。 [証明書登録ガイド](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)) をクリックします。

   * ***ExpressPlay アカウント*** -Adobeから、ExpressPlay 管理者アカウントの登録に使用するリンクが記載された電子メールが送信されます。

1. Adobe IDを使用してAdobe証明書ポータルにログインします (Adobeの担当者に指定したのと同じ電子メールアドレスを使用します )。 まだAdobe IDをお持ちでない場合は、 *Adobe IDを入手* 証明書ポータルからのリンク：

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Adobe証明書ポータルで、 *体験版* 証明書

   Multi-DRM 体験版の場合、1 つの体験版証明書で、パッケージ化、ライセンス、および転送といったコンテンツ保護のすべての側面をカバーします。 独自のを指定する必要があります [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) 証明書の要求を行うには：
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobeから、証明書の要求の受け入れまたは拒否を示す電子メールが送信されます。 証明書要求のステータスは、 *リクエスト履歴* 証明書ポータルのタブ：
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. ExpressPlay 管理者アカウントを作成します。

   指定された ExpressPlay へのリンクをたどって、Adobeを表示します。 これにより、 *アカウントの作成* ページを ExpressPlay に貼り付けます。 必要な情報を入力し、フォームを送信します。 次のメールが届きます： `operations@expressplay.com` 1 週間有効なアクティベーションリンクが含まれています。 アクティブ化したら、ExpressPlay サービスを設定します。
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   サービスを作成すると、独自の管理ページが表示されます。 一部のアクティビティトラッキングフィールドと共に、実稼動環境とテスト環境が表示されます *顧客認証子* （API キー）、実稼動環境およびテストサービスの URL は次のとおりです。

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. FairPlay を使用している場合は、(Apple開発者サイトで )ExpressPlay を設定するための追加の手順が必要です。 詳しくは、 [FairPlay 向け ExpressPlay サービスの有効化](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) 」を参照してください。
