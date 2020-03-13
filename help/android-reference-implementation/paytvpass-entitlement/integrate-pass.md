---
description: 参照実装をカスタマイズして、実稼働環境にAdobe Primetime認証を統合します。
seo-description: 参照実装をカスタマイズして、実稼働環境にAdobe Primetime認証を統合します。
seo-title: Primetime認証の統合
title: Primetime認証の統合
uuid: 34cdf1da-261e-462c-a194-4fcb439e5dfb
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Primetime認証の統合 {#integrate-primetime-authentication}

参照実装をカスタマイズして、実稼働環境にAdobe Primetime認証を統合します。

Primetime認証サービスのリファレンス実装の統合は、デモとしてそのまま使用できます。 ただし、実稼働用プレーヤーで統合を使用するには、次のカスタマイズを実装する必要があります。

1. エンタイトルメントフローの有効化または無効化

   を有効 `EntitlementManager` にするには、まずPrimetime認証SDKのインスタンスを初期化し、取得する必要があります。 がこのライ `EntitlementManager` ブラリを初期化しない場合、マネージャは無効になります。
1. メインアプリケ `EntitlementManger`ーションクラスからを有効にします。

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. クラスを使 `ManagerFactory` 用して、のインスタンスを取得しま `EntitlementManager`す。

   アプリケーションのEntitlementManager `ManagerFactory` の単一のインスタンスを管理し `EntitlementManager`ているので、常にを使 `ManagerFactory` 用して、のインスタンスを取得する必要があります。 またはクラスのコンストラクタ `EntitlementManager` を使用し `EntitlementManagerOn` て、クラスをインスタンス化しないでください。

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   以前に `ManagerFactory` を呼び出した場合、 `EntitlementManagerOn`エンタイトルメントフローが有効なので、のインスタンスが返されま `EntitlementManager.initializeAccessEnabler`す。 最初にを呼び出さない場合、はのイ `EntitlementManager.initializeAccessEnabler`ンスタンスを返 `ManagerFactory` し、エンタイトルメ `EntitlementManager`ントフローは無効になります。 1.要求者IDを設定します。

   参照の実装には、テスト要求者IDが次のように設定されています。&quot;REF&quot; この要求者IDを使用して、アプリケーションをテストできます。 Primetime認証担当者から提供された要求者IDを使用する準備が整ったら、要求者IDを使用してアプリケーションのフ [!DNL res/values/strings.xml] ァイルを更新します。

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

   また、Primetime認証サービスへの接続に使用するURLの変更が必要な場合もあります。 これには、Primetime認証ステージングおよび実稼働サーバーのURL、トークン検証サービスのURLが含まれます。 詳しくは、Adobe Primetimeの担当者にお問い合わせください。 1.要求者IDに署名します。

   Primetime認証システム内のプログラマのIDを確立するために、プログラマの要求者IDがPrimetime認証システムに送信されます。 セキュリティの層を強化するため、要求者IDは、アドビに送信する前に、プログラマーが署名する必要があります。 アドビでは、プログラマーが信頼されたネットワーク上で要求者IDに署名するサービスを設定することをお勧めします。

   Primetime Reference Implementationでは、要求者IDへの署名方法を示していますが、これはデモ目的でのみ使用されます。 署名証明書と署名ジェネレーターコードは、の下にある本番アプリケーシ `com.adobe.primetime.reference.crypto`ョンに含めないことを強くお勧めします。 その代わり、信頼できるネットワークサービスに移行する必要があります。

1. サーバー環境の設定を参照してください。

   Primetime認証サービスは、次の2つの異なる環境で実行できます。

   * ステージング — ステージング環境は、アプリケーションのテストに使用されます。
   * 実稼働環境 — 実稼働環境は、アプリケーションの実稼働環境でのデプロイメントに使用されます。
   ステージング環境と実稼働環境の両方に対して、アプリケーションを使用してURIを設定しますが、コード内のアプリケーションで使用するURIを設定する必要があります。 クラス `com.adobe.primetime.reference.manager.EntitlementManger` で、変数を、使用し `environmentUri` ているPrimetime認証サ `STAGING_URI` ービ `PRODUCTION_URI` ス環境に応じて、またはどちらかに設定します。

   >[!NOTE]
   >
   >指定した要求者ID(「REF」)は、ステージング環境でのみ使用する必要があります。

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

1. MVPD選択グリッドをカスタマイズします。

   コンテンツプロバイダーの選択ページには、ユーザーが選択できる上位9件のMVPDのテーブルが表示されます。 アプリケーションは、Primetime認証システムのプログラマーと統合された使用可能なMVPDと一致する、順番に並べられたリストから上位9つのMVPDを取り込みます。 プライマリMVPDの順番に並べられたリストは、MVPD表示名ではなく、Primetime認証システム内のMVPD IDに対してキー設定されます。 プライマリMVPDリストのMVPD IDがプログラマのアカウントに統合されたMVPD IDと一致することを確認することが重要です。場合によっては、IDが統合間で異なることがあります。 以下に、クラス内のプライマリMVPDの順番に並べられたリストを示しま `com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`す。

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

   次の表に、プライマリMVPDの順番に並べられたリストの使用例を示します。 最初の列には、プログラマと統合されたMVPDが表示されます。 2番目の列は、MVPDの（短縮された）順序付きリストです。 3番目の列は、上位6つのMVPDをユーザーに表示するために使用される結果リストです。

   この例では、例を簡単にするために、実際の9個ではなく上位6個のMVPDを使用しています。 結果リストには、最初の2つのリストの共通部分が含まれ、2番目のリストと同じ順序が設定されています。 また、AT&amp;T U-verseは最終リストには含まれていないので、最初に一致した6つのMVPDのみが取得されます。

| 使用可能なMVPD | プライマリMVPD | 6つのMVPDを表示 |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>皿</li><li>AT&amp;T U-verse</li><li>ケーブルワン</li><li>Brighthouse</li><li>大西洋広帯域</li><li>わぁ！</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>ケーブルビジョン最適</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li> TWC</li><li>Cox</li><li>憲章</li><li>Verizon FiOS</li><li>ケーブルビジョン最適</li><li>AT&amp;T U-verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li>TWC</li><li>Cox</li><li>ケーブルビジョン最適</li></ol> |
