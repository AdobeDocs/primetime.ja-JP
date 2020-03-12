---
description: ライセンスは、保護されたビデオコンテンツの再生を許可または拒否する主なメカニズムです。 正規の（権利付与済みの）ユーザーは、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生するためのライセンス（キー）を発行できます。
seo-description: ライセンスは、保護されたビデオコンテンツの再生を許可または拒否する主なメカニズムです。 正規の（権利付与済みの）ユーザーは、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生するためのライセンス（キー）を発行できます。
seo-title: ライセンス
title: ライセンス
uuid: 9f433d62-5609-4d88-95fd-c1e7c0f6aa75
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# ライセンス{#licensing}

ライセンスは、保護されたビデオコンテンツの再生を許可または拒否する主なメカニズムです。 正規の（権利付与済みの）ユーザーは、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生するためのライセンス（キー）を発行できます。

エンドユーザーのデバイス上のアプリまたはWebページでDRM保護コンテンツを再生する前に、顧客が操作するエンタイトルメントサーバーまたはストアフロントサーバーからトークンを取得する必要があります。 アドビでは、次の目的のためのサンプルリファレンスサーバーを提供しています。リファレ [ンスサーバ：ExpressPlay Entitlement Server(SEES)の例](../../multi-drm-workflows/feature-topics/sees-reference-server.md)。

エンタイトルメントまたはストアフロントサーバーは、特定のユーザーに要求されたコンテンツの視聴権限が付与されているかどうかを確認するために、お使いのバックエンドシステムでのみ、関連するExpressPlay Serverのライセンストークンを要求します。 ライセンストークンリクエストから返される応答は、ライセンスサーバーの使用準備完了のURLか、使用しているDRMソリューションに応じてJSON構造のURLが応答に含まれています。

>[!NOTE]
>
>ライセンストークンリクエストは、クライアント自体からは作成できません。
>1. 権限は、信頼できる環境でチェックする必要があります。および
>1. ユーザー認証子は秘密にしておく必要があります。


1. ライセンストークンリクエストを作成します。

   関連する様々なコンポーネントが連携して動作することを確認する必要があるクイックスタートシナリオの場合は、（最初にアプリを起動し、実行し、呼び出しをテストするのとは対照的に）ライセンストークンリクエストを作成するのと同じような方法を使用します。 [!DNL curl] 例：

   * Widevine:

   ```
   curl "https://wv-gen.test.expressplay.com/hms/wv/token?customerAuthenticator= 
   <Customer Authenticator> 
   &kid 
   <indexterm>
   CEKSID 
     <indexterm>
     as query parameter kid 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEKSID> 
      &contentKey 
    <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    Widevine 
    </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>WidevineToken 
   ```

   Widevineテストトークンの例：

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Widevineの応答は、「使用可能」なURL文字列です。

   * PlayReady:

   ```
   curl "https://pr-gen.test.expressplay.com/hms/pr/token?customerAuthenticator= 
   <Customer Authenticator> 
      &kid 
   <indexterm>
   CEKSID 
   <indexterm>
   as query parameter kid 
   <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<Key ID> 
      &contentKey 
   <indexterm>
    CEK 
    <indexterm>
    as query parameter contentKey 
    <indexterm>
    PlayReady 
   </indexterm> 
   </indexterm> 
   </indexterm>=<CEK> 
      &<Any additional licensing attributes desired>" >>playreadyToken
   ```

   PlayReadyテストトークンの例：

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   PlayReadyの応答は、URL要素とトークン要素が別々に存在するJSONオブジェクトです。

   * FairPlay:

   ```
   curl "https://fp-gen.test.expressplay.com/hms/fp/token?customerAuthenticator= 
    <Customer Authenticator> 
    &kid 
    <indexterm>
      CEKSID 
    <indexterm>
      as query parameter kid 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<Key ID> 
          &contentKey 
    <indexterm>
      CEK 
    <indexterm>
      as query parameter contentKey 
      <indexterm>
        FairPlay 
      </indexterm> 
    </indexterm> 
    </indexterm>=<CEK> 
    &iv=<IV ID> 
    &<Any additional licensing attributes desired>"
   ```

   FairPlayテストトークンの例：

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   FairPlayの応答は、「使用可能な」URL文字列です。
