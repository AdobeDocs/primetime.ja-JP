---
description: リファレンス実装をカスタマイズして、実稼働環境用のAdobe Primetime認証を統合します。
title: Primetime認証の統合
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '767'
ht-degree: 0%

---


# Primetime認証の統合{#integrate-primetime-authentication}

リファレンス実装をカスタマイズして、実稼働環境用のAdobe Primetime認証を統合します。

Primetime認証サービスのリファレンス実装の統合は、デモとしてそのまま使用できます。 ただし、実稼働用プレイヤーで統合を使用するには、次のカスタマイズを実装する必要があります。

1. エンタイトルメントフローを有効または無効にします。

   `EntitlementManager`は、最初に、有効にするPrimetime認証SDKのインスタンスを初期化し、取得する必要があります。 `EntitlementManager`がこのライブラリを初期化しない場合、マネージャは無効になります。
1. メインアプリケーションクラスから`EntitlementManger`を有効にします。

   ```java
   // initialize the AccessEnabler library, required for Primetime PayTV Pass entitlement workflows 
   EntitlementManager.initializeAccessEnabler(this); // comment out this line to disable entitlement workflows
   ```

1. `ManagerFactory`クラスを使用して`EntitlementManager`のインスタンスを取得します。

   `ManagerFactory`がアプリケーションに対してEntitlementManagerの単一のインスタンスを維持するので、`ManagerFactory`を使用して`EntitlementManager`のインスタンスを取得する必要があります。 `EntitlementManager`クラスまたは`EntitlementManagerOn`クラスのインスタンスを作成する場合は、必ずそのコンストラクタを使用してください。

   ```java
   EntitlementManager entitlementManager =  
   ManagerFactory.getEntitlementManager();
   ```

   `ManagerFactory`は、以前に`EntitlementManager.initializeAccessEnabler`と呼ばれていた場合、エンタイトルメントフローを有効にして、`EntitlementManagerOn`のインスタンスを返します。 最初に`EntitlementManager.initializeAccessEnabler`を呼び出さない場合、`ManagerFactory`は`EntitlementManager`のインスタンスを返し、エンタイトルメントフローは無効になります。 1.要求者IDを設定します。

   リファレンスの実装には、テスト要求者IDが次の値に設定されている事前設定が含まれています。&quot;REF&quot;. この要求者IDを使用してアプリケーションをテストできます。 Primetime認証担当者から提供された要求者IDを使用する準備が整ったら、アプリケーションの[!DNL res/values/strings.xml]ファイルを要求者IDで更新します。

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

   さらに、Primetime認証サービスへの接続に使用するURLの変更が必要になる場合があります。 これには、Primetime認証ステージングおよび実稼働サーバーのURL、トークン検証サービスへのURLが含まれます。 詳しくは、Adobe Primetimeの担当者にお問い合わせください。 1.要求者IDに署名します。

   Primetime認証システム内でプログラマのIDを確立するために、プログラマの要求者IDがPrimetime認証システムに送信されます。 セキュリティの追加層として、要求者IDは、Adobeに送信する前にプログラマが署名する必要があります。 Adobeでは、プログラマーが信頼されたネットワーク上の要求者IDに署名するサービスをセットアップすることを推奨します。

   Primetime Reference Implementationでは、リクエスト元IDに署名する方法を示していますが、これはデモ目的でのみ使用されます。 Adobeでは、`com.adobe.primetime.reference.crypto`の下にある署名証明書と署名ジェネレーターコードを、実稼働アプリケーションに含めないことを強くお勧めします。 その代わりに、信頼できるネットワーク・サービスに移行する必要があります。

1. サーバー環境を設定します

   Primetime認証サービスは、次の2つの異なる環境で実行できます。

   * ステージング — ステージング環境は、アプリのテストに使用します。
   * 実稼働環境 — 実稼働環境は、アプリケーションの実稼働環境でのデプロイメントに使用されます。

   ステージング用と実稼働用の両方の環境のURIは、アプリケーションを使用して設定しますが、コード内のアプリケーションで使用するURIを設定する必要があります。 `com.adobe.primetime.reference.manager.EntitlementManger`クラスで、`environmentUri`変数を`STAGING_URI`または`PRODUCTION_URI`に設定します。どちらのPrimetime認証サービス環境を使用しているかに応じて異なります。

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

   コンテンツプロバイダーの選択ページには、ユーザーが選択できる上位9つのMVPDのテーブルが表示されます。 アプリケーションは、Primetime認証システムのプログラマーと統合された使用可能なMVPDに一致する、順番に並べられたリストから上位9個のMVPDを取り込みます。 プライマリMVPDの順番に並べられたリストは、MVPD表示名ではなく、Primetime認証システム内のMVPDにキー設定されます。 プライマリMVPDリストのMVPD IDが、プログラマーのアカウントに統合されたMVPD IDと一致することを確認することが重要です。場合によっては、統合間でIDが異なることがあります。 以下は、クラス`com.adobe.primetime.reference.ui.entitlement.MvpdPickerFragment`にある主なMVPDの順番に並べられたリストです。

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

   次の表に、プライマリMVPDの順番に並べられたリストの使用例を示します。 最初の列リストは、MVPDがプログラマと統合されています。 2番目の列は、MVPDの（短縮された）順序付けされたリストです。 3番目の列は、上位6つのMVPDをユーザーに表示するために使用される結果リストです。

   この例では、実際の9個のMVPDの代わりに上位6個のMVPDを使用して、例を簡単にします。 結果リストに、最初の2つのリストの交点が含まれ、2つ目のリストと同じ順序になっていることに注目してください。 また、AT&amp;T U-verseは最終リストには含まれず、最初に一致した6つのMVPDのみが取得されます。

| 利用可能なMVPD | プライマリMVPD | 6つのMVPDを表示 |
|--- |--- |--- |
| <ol><li>Comcast XFINITY</li><li>TWC</li><li>Mediacom</li><li>RCN</li><li>皿</li><li>AT&amp;T U-verse</li><li>ケーブルワン</li><li>Brighthouse</li><li>大西洋ブロードバンド</li><li>わあ！</li><li>MetroCast</li><li>DirectTV </li><li>Cox</li><li>Cablevision Optimum</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li> TWC</li><li>Cox</li><li>憲章</li><li>Verizon FiOS</li><li>Cablevision Optimum</li><li>AT&amp;T U-verse</li></ol> | <ol><li>Comcast XFINITY</li><li>DirectTV</li><li>皿</li><li>TWC</li><li>Cox</li><li>Cablevision Optimum</li></ol> |
