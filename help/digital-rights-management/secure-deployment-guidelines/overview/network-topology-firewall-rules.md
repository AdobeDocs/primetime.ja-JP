---
description: ファイアウォール規則を決定する際には、次の種類の URL を考慮してください
title: ファイアウォール規則
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ファイアウォール規則 {#firewall-rules}

ファイアウォール規則を決定する際には、次の種類の URL を考慮してください。

## 受信 URL {#section_F111526A9DB844CBBF21A3CAE5F50880}

外側のファイアウォールを設定して、エンドユーザーに提供するアプリケーション機能の URL のみを公開することができます。

外部ユーザーは、外部のファイアウォールを使用して、次の URL にアクセスできます。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_bqs_whz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">ルート URL </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">目的 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">サーバーのバージョンを確認するには、以下を実行します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_xr4_hdn_44"> 
     <li id="li_8C68877B0FAF427490BF826FB12BE2F2"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li_BF44753FF42E40BD911D04996B962188"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li_9B633CDDB3844644BD8E3BFE80FD1672"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li_01B2E17BF4DB456383FD6E18E9DE28F5"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
     <li id="li_096D349CCD7945B387CB80C3E99063C7"><span class="filepath"> /flashaccess/authn/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザを認証する。 </p> <p>ユーザー認証にAdobe Primetime DRM Client API を使用する場合は、この URL にアクセスできる必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_yxs_rdn_44"> 
     <li id="li_4BEB80F46E8D4D0F90F9998AB7FAAEB7"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li_20DDE5B03284436F9DEF794867AFBC53"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li_6555F8689FF945338579C58DADC2E36D"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li_5112283BDCF1457099056733B633FAF1"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
     <li id="li_F73A570E2C1A45E1BBF21C1468B90D3A"><span class="filepath"> /flashaccess/license/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">エンドユーザーにライセンスを発行する場合。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_ibl_5dn_44"> 
     <li id="li_3B984F500F6848EDBBA5ADC570417E34"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li_3204CF10D68C4FDB97E369BD63FA3C2B"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li_2222D27F73D0421396A4F0E18140B3F9"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
     <li id="li_18020B7CE36B4C209F65FF01A00B6737"><span class="filepath"> /flashaccess/sync/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">リクエストを同期します。 </p> <p>ライセンスで同期要件を指定する場合は、この URL にアクセスできる必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_plq_ydn_44"> 
     <li id="li_61F51463E2BF4ABCA4F209754D8A8052"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li_898E849D7EA24045978D35C336AEEAFE"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li_CF7590FDAF694EDF9685434BE8EE10CA"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
     <li id="li_CA73424FDFAA4BD8BBE2C1AD165D2C31"><span class="filepath"> /flashaccess/domain/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ドメインを登録する。 </p> <p>ドメインサポートを実装している場合は、この URL にアクセスできる必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_btm_c2n_44"> 
     <li id="li_8A0DC38312CB4D3DBD313B3DE089D39E"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li_5BA24F70381F465F832FF28925B622C1"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li_C761F14F3C97479CBA5C255739E01A28"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
     <li id="li_23A8AABE7499488EB61B7ED27CC65098"><span class="filepath"> /flashaccess/dereg/v6/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ドメインの登録を解除するには： </p> <p>ドメインサポートを実装している場合は、この URL にアクセスできる必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerconversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントが FMRMS 1.x の DRM メタデータを Primetime DRM メタデータに変換できるようにする。 </p> <p>注意：この URL では SSL(HTTPS) を使用する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">LiveCycle Rights Management ESWeb サービスの URL。 以前のバージョンの FMRMS を使用してコンテンツが公開された場合、この URL を使用すると、古いクライアントがサーバーに接続できます。 これらのクライアントは、Adobe Primetime DRM にアップグレードするよう求められます。 </p> <p class="- topic/p ">注意：この URL では SSL(HTTPS) を使用する必要があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul_382B69AB07204DD596BB375132224D96"> 
     <li id="li_24B4D42BECF8405281C73B782F8E7310"><span class="filepath"> /flashaccess/lreturn/v5</span> </li> 
     <li id="li_6B79563205D1421F89131E650D71E83B"><span class="filepath"> /flashaccess/lreturn/v6</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p>ライセンスを返す。 </p> <p> ライセンスのリターンサポートを実装している場合は、URL にアクセスできる必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>内部ファイアウォールでは、リバースプロキシを介した Primetime DRM ライセンスサーバーへの接続のみを許可し、テーブル内の URL への接続のみを許可する必要があります。 スケーラビリティを向上させるには、リバースプロキシと Primetime DRM 間の接続に HTTP を使用します。

## 送信 URL {#section_FFF9F7BB353149F4A27F8788E9934A48}

送信 URL を使用すると、ライセンスサーバーはAdobeから CRL をダウンロードできます。

使用できる送信 URL のリストを次に示します。

* `https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl`
* `https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl`
* `https://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl`
* `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`
