---
description: ライセンスは、保護されたビデオコンテンツの再生をユーザーが許可または拒否する主なメカニズムです。 正当な（権利付与済みの）ユーザーに、ライセンス（キー）を発行して、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生することができます。
seo-description: ライセンスは、保護されたビデオコンテンツの再生をユーザーが許可または拒否する主なメカニズムです。 正当な（権利付与済みの）ユーザーに、ライセンス（キー）を発行して、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生することができます。
seo-title: ライセンス
title: ライセンス
uuid: 9f433d62-5609-4d88-95fd-c1e7c0f6aa75
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---


# ライセンス{#licensing}

ライセンスは、保護されたビデオコンテンツの再生をユーザーが許可または拒否する主なメカニズムです。 正当な（権利付与済みの）ユーザーに、ライセンス（キー）を発行して、コンテンツプロバイダーの暗号化されたコンテンツの特定の部分を復号化し、再生することができます。

エンドユーザーのデバイス上のアプリまたはWebページでDRM保護されたコンテンツを再生する前に、ユーザーが操作するエンタイトルメントサーバーまたはストアフロントサーバーからトークンを取得する必要があります。 Adobeには、この目的のためのサンプルのリファレンスサーバーが用意されています。[リファレンスサーバー：ExpressPlayエンタイトルメントサーバー(SEES)のサンプル](../../multi-drm-workflows/feature-topics/sees-reference-server.md)

エンタイトルメントサーバーまたはストアフロントサーバーは、関連するExpressPlay Serverに対して、特定のユーザーが要求されたコンテンツを視聴する権利があるかどうかをバックエンドシステムで確認した後にのみ、ライセンストークンを要求します。 ライセンストークンリクエストから返されるレスポンスは、使用可能なライセンスサーバーのURLか、使用するDRMソリューションに応じて、レスポンスにURLがJSON構造で含まれています。

>[!NOTE]
>
>ライセンストークンリクエストは、クライアント自体からは実行できません。
>1. 権限は、信頼できる環境でチェックインする必要があります。と
>1. ユーザー認証子は秘密にする必要があります。


1. ライセンストークンリクエストを作成します。

   関連する様々なコンポーネントが連携していることを確認したいだけの開始シナリオの場合は、[!DNL curl]のようなものを使用してライセンストークンリクエストを行います（アプリの起動と実行、呼び出しのテストを行う場合とは異なります）。 例：

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

   Widevineのテスト用トークンの例：

   ```
   https://wv.test.expressplay.com/widevine/RightsManager.asmx?ExpressPlayToken= 
      AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
      RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
      O1PqRkx59Q2q1s2cFNrqfml8Y3RQ 
   ```

   Widevineの応答は、「使用に対応した」URL文字列です。

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

   PlayReadyテスト用トークンの例：

   ```
   {"licenseAcquisitionUrl":"https://pr.test.expressplay.com/playready/RightsManager.asmx", 
   "token":"AQAAAxBbWv4AAABgV8_GaWjU80mObLQdfwEdy1lenXmcqvx5VLyqixigtwXLthzjPxq9QDT-TYbudNrMSOpUAy 
   G_2Qt8RdTGJ2_Q_xtRfnj7H6C-yt6By40IhNaSQ0nNYUsY1_MtCrHXIltlVhN2Ekr_RNyTNvCjYs0V5TqzOPY"} 
   ```

   PlayReadyのレスポンスは、URL要素とトークン要素が別々に設定されたJSONオブジェクトです。

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

   FairPlayのテスト用トークンの例：

   ```
   https://{expressplay_test_domain_license_url}/?ExpressPlayToken= 
   AQAAAJJ2Y0MAAABQbyvnJ6KgEg_w-2yZmU-MsjTEZ3f7UkhUcFhDFAvdonzBk 
   RGQU-xe1G-DMbel5-BVH_PozovdWhKZx0_SXRokfh9-FERmBl6OEfGfPqMI1e 
   O1PqRkx59Q2q1s2cFNrqfml8Y3RQ
   ```

   FairPlayの応答は、「使用できる」URL文字列です。
