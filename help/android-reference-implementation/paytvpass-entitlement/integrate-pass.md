---
description: 参照実装をカスタマイズして、実稼動環境にAdobe Primetime認証を統合します。
title: Primetime 認証の統合
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---

# Primetime 認証の統合 {#integrate-primetime-authentication}

参照実装をカスタマイズして、実稼動環境にAdobe Primetime認証を統合します。

Primetime 認証サービスのリファレンス実装統合は、デモとして標準で動作します。 ただし、実稼動用のプレーヤーで統合を使用するには、次のカスタマイズを実装する必要があります。

1. エンタイトルメントフローを有効または無効にします。

   The `EntitlementManager` は、最初に初期化し、有効にする Primetime 認証 SDK のインスタンスを取得する必要があります。 次の場合、 `EntitlementManager` このライブラリを初期化しない場合、マネージャは無効になります。
1. を有効にします。 `EntitlementManger`を、メインのアプリケーションクラスから次のように選択します。

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. 以下を使用します。 `ManagerFactory` クラスを使用して `EntitlementManager`.

   常に `ManagerFactory` 例を得るには `EntitlementManager`、 `ManagerFactory` は、アプリケーション用に EntitlementManager の 1 つのインスタンスを管理します。 絶対に `EntitlementManager` または `EntitlementManagerOn` コンストラクタを使用してクラスを作成する。

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   The `ManagerFactory` のインスタンスを返します。 `EntitlementManagerOn`（以前にと呼ばれていた場合） `EntitlementManager.initializeAccessEnabler`. 最初にを呼び出さない場合は、 `EntitlementManager.initializeAccessEnabler`を、 `ManagerFactory` は次のインスタンスを返します： `EntitlementManager`（エンタイトルメントフローは無効） 1.リクエスト元 ID を設定します。

   参照実装には、テスト要求者 ID が「REF」に設定された状態で事前設定されています。 この要求者 ID を使用して、アプリケーションをテストできます。 Primetime 認証担当者から提供された要求者 ID を使用する準備が整ったら、アプリケーションの [!DNL res/values/strings.xml] ファイルにリクエスト元 ID が含まれていることを確認します。

   ```xml
   <!-- Programmer Requestor ID, change to ID provided by your Adobe  
        Primetime pay-TV pass representative --> 
   <string name="adobepass_requestor_id">REF</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for production 
        environment --> 
   <string name="adobepass_sp_url_production">sp.auth.adobe.com</string> 
   
   <!-- Adobe Primetime pay-TV pass service provider endpoint for staging  
        environment --> 
   <string name="adobepass_sp_url_staging">sp.auth-staging.adobe.com</string>
   ```

   さらに、アプリケーションが Primetime 認証サービスに接続する際に使用する URL を変更する必要が生じる場合があります。 これには、Primetime 認証のステージングおよび実稼動サーバーの URL、トークン検証サービスへの URL が含まれます。 詳しくは、Adobe Primetimeの担当者にお問い合わせください。 1.要求者 ID に署名します。

   Primetime 認証システム内でプログラマーのアイデンティティを確立するために、プログラマーの要求者 ID が Primetime 認証システムに送信されます。 セキュリティの追加層として、要求者 ID は、要求者 ID をAdobeに送信する前に、プログラマーによって署名される必要があります。 Adobeは、プログラマーが、信頼されたネットワーク上の要求者 ID に署名するサービスを設定することを推奨します。

   Primetime Reference Implementation では、Requestor ID への署名方法を示していますが、これはデモ目的でのみ使用されます。 Adobeでは、署名証明書と署名生成コードを、 `com.adobe.primetime.reference.crypto`を実稼動アプリケーションに含めないでください。 代わりに、信頼できるネットワーク・サービスに移動する必要があります。

1. サーバー環境を設定します。

   Primetime 認証サービスは、次の 2 つの異なる環境で実行できます。

   * ステージング — ステージング環境は、アプリケーションのテストに使用されます。
   * 実稼動環境 — 実稼動環境は、アプリケーションのライブデプロイメントに使用されます。

   アプリケーションを使用して、ステージング環境と実稼動環境の両方に URI を設定しますが、アプリケーションがコード内で使用する URI を設定する必要があります。 Adobe Analytics の `com.adobe.primetime.reference.manager.EntitlementManger` クラス、 `environmentUri` 変数を `STAGING_URI` または `PRODUCTION_URI` 使用する Primetime 認証サービス環境に応じて異なります。

   >[!NOTE]
   >
   >指定した要求者 ID(「REF」) は、ステージング環境でのみ使用する必要があります。

   `com.adobe.primetime.reference.manager.EntitlementManager`:

   ```java
     // Adobe Primetime authentication service provider endpoint for production environment 
     PRODUCTION_URI = 
         application.getResources().getString(R.string.adobepass_sp_url_production); 
   
     // Adobe Primetime authentication service provider endpoint for staging environment 
     STAGING_URI = 
       application.getResources().getString(R.string.adobepass_sp_url_staging); 
   
     // Set to STAGING_URI when testing against the staging/test environment 
     // Set to PRODUCTION_URI when deploying the application for production use 
     String environmentUri = STAGING_URI; 
   
     // Adobe Primetime authentication service URI used by this application 
     PAYTV_PASS_URI = environmentUri + "/adobe-services"; 
   
     // Token Verification Service URL 
     TVS_URL = "https://" + environmentUri + "/tvs/v1/validate";
   ```

1. MVPD 選択グリッドをカスタマイズします。

   コンテンツプロバイダーの選択ページには、ユーザーが選択できる上位 9 つの MVPD のテーブルが表示されます。 アプリケーションは、Primetime 認証システムでプログラマーと統合された使用可能な MVPD と一致する、アプリケーション内の順序付きリストから上位 9 つの MVPD を取り込みます。 プライマリ MVPD の順番付けされたリストは、MVPD 表示名ではなく、Primetime 認証システム内の MVPD ID に基づいてキー設定されます。 プライマリ MVPDs リスト内の MVPD ID がプログラマーのアカウントと統合された MVPD ID と一致することを確認することが重要です。場合によっては、統合間で ID が異なる可能性があります。 以下は、クラス内のプライマリ MVPD の順番付きリストです `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`.

   ```java
   /* Array of MVPDs to display in a Grid of icons 
   When displaying a grid, only the MVPDs which intersect this array and the 
   ArrayList of all MVPDs are displayed. 
   The array contents are ordered by display preference as only a maximum of 
   MAX_DISPLAY_ICONS are displayed. 
   */ 
   private static final String[] PRIMARY_MVPDS = { 
   "Comcast_SSO",                         // Comcast XFINITY 
   "DTV",                                 // DirectTV 
   "Dish",                                // Dish 
   "TWC",                                 // Time Warner Cable 
   "Cox",                                 // Cox 
   "Charter_Direct",                      // Charter 
   "Verizon",                             // Verizon FiOS 
   "Cablevision",                         // Cablevision Optimum 
   "ATT",                                 // AT&T U-verse 
   "Brighthouse",                         // Brighthouse 
   "Suddenlink",                          // Suddenlink 
   "Mediacom",                            // Mediacom 
   "CableOne",                            // CableOne 
   "WOW",                                 // WOW! 
   "RCN",                                 // RCN 
   "auth_atlanticbb_net",                 // Atlantic Broadband 
   "auth_armstrongmywire_com",            // Armstrong 
   "knology_auth-gateway_net",            // KNOLOGY 
   "serviceelectric_auth-gateway_net",    // Service Electric Cablevision 
   "msauth_midco_net",                    // Midcontinent Communications 
   "auth_metrocast_net",                  // MetroCast 
   "www_websso_mybrctv_com",              // Blue Ridge Communications 
   };
   ```

   次の表に、プライマリ MVPD の順番付きリストの使用例を示します。 最初の列には、プログラマと統合された MVPD が一覧表示されます。 2 番目の列は、MVPD の（短縮された）順番付きリストです。 3 番目の列は、上位 6 つの MVPD をユーザーに表示するために使用される結果リストです。

   この例では、例をシンプルにするために、実際の 9 つの MVPD の代わりに、上位 6 つの MVPD を使用します。 結果リストには、最初の 2 つのリストの積集合が含まれ、2 番目のリストと同じ順序になっていることに注意してください。 また、AT&amp;T U-verse は最終リストに含まれていないことに注意してください。最初に一致した 6 つの MVPD しか取得されません。

| 使用可能な MVPD | プライマリMVPDs | 6 個の MVPD を表示 |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>皿</li><li>AT&amp;T U -verse</li><li>CableOne</li><li>Brighthouse</li><li>大西洋広帯域</li><li>うわー！</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li> TWC</li><li>Cox</li><li>憲章</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T U -verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
