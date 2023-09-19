---
description: ライセンスは、保護されたビデオコンテンツの一部を再生するユーザーが許可または拒否される主なメカニズムです。 正当な（権利を付与された）ユーザーに対して、ライセンス（キー）を発行して、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化して再生することができます。
title: ライセンス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ライセンス{#licensing}

ライセンスは、保護されたビデオコンテンツの一部を再生するユーザーが許可または拒否される主なメカニズムです。 正当な（権利を付与された）ユーザーに対して、ライセンス（キー）を発行して、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化して再生することができます。

エンドユーザーのデバイス上のアプリまたは Web ページで DRM 保護されたコンテンツを再生する前に、ユーザーが操作する権利付与またはストアフロントサーバーからトークンを取得する必要があります。 Adobeには、この目的のためのサンプル参照サーバーが用意されています。 [参照サーバー： ExpressPlay 使用権限サーバーの例 (SEES)](../../multi-drm-workflows/feature-topics/sees-reference-server.md).

使用権限またはストアフロントサーバーは、特定のユーザーがリクエストされたコンテンツを視聴する資格があるかどうかを確認するために独自のバックエンドシステムで確認した後にのみ、関連する ExpressPlay サーバーからライセンストークンをリクエストします。 ライセンストークンリクエストから返される応答は、ライセンスサーバーのすぐに使用できる URL か、使用している DRM ソリューションに応じて、URL が JSON 構造で含まれます。

>[!NOTE]
>
>ライセンストークンのリクエストは、クライアント自体からは実行できません。
>1. 権限は、信頼できる環境で確認する必要があります。
>1. ユーザー認証子は秘密にしておく必要があります。

1. ライセンストークンリクエストを作成します。

   関連する様々なコンポーネントが連携して動作していることを確認したい場合は、次のような操作を行うと便利です。 [!DNL curl] （最初にアプリを起動して実行し、そこから呼び出しをテストするのとは異なります）。 例：

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

   サンプル Widevine テストトークン：

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Widevine の応答は、「使用準備完了」の URL 文字列です。

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

   PlayReady テストトークンの例：

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   PlayReady の応答は、URL とトークン要素が別々に設定された JSON オブジェクトです。

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

   FairPlay テストトークンの例：

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   FairPlay の応答は、「使いやすい」URL 文字列です。
