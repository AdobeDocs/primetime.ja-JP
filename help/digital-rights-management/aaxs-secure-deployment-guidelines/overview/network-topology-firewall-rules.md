---
seo-title: ファイアウォール規則
title: ファイアウォール規則
uuid: a5667030-c4d0-42e3-b56e-20a12c903954
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ファイアウォール規則 {#firewall-rules}

## 受信URL {#section-F111526A9DB844CBBF21A3CAE5F50880}

エンドユーザーに提供するアプリケーション機能のURLのみを公開するように、外側のファイアウォールを設定します。 外部ユーザーが外部ファイアウォールを介してアクセスできるように、次の表に示すURLのみを許可します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table-bqs-whz-n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">ルートURL </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">目的 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/getServerVersion/v3</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">サーバーのバージョンを決定するURL。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-xr4-hdn-44"> 
     <li id="li-05925A4DE4114F7786FF93A66AB8A117"><span class="filepath"> /flashaccess/authn/v1/*</span> </li> 
     <li id="li-E76E9BA0160F4E7F9EBB64428C2D9F31"><span class="filepath"> /flashaccess/authn/v3/*</span> </li> 
     <li id="li-ED3C15EB4D194FFE99954BDB7D5C1E41"><span class="filepath"> /flashaccess/authn/v4/*</span> </li> 
     <li id="li-4DD6CBBE939F4E6EABA474E3DCCBD893"><span class="filepath"> /flashaccess/authn/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ユーザー認証のURL。 このURLは、Adobe Access Client APIを使用してユーザー認証を実行する場合にのみアクセス可能である必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-yxs-rdn-44"> 
     <li id="li-49B9987ED6E14FADA66727448F923F84"><span class="filepath"> /flashaccess/license/v1/*</span> </li> 
     <li id="li-BF4A415E573C4C728E24D548F53D923C"><span class="filepath"> /flashaccess/license/v3/*</span> </li> 
     <li id="li-E6C551DDA030429B9D0073D2685B778A"><span class="filepath"> /flashaccess/license/v4/*</span> </li> 
     <li id="li-57811F4CD7304DBDAFADD65244AED0D9"><span class="filepath"> /flashaccess/license/v5/*</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">エンドユーザーにライセンスを発行するためのURL。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-ibl-5dn-44"> 
     <li id="li-189BE370CD5044F988A42335C3BFE420"><span class="filepath"> /flashaccess/sync/v3</span> </li> 
     <li id="li-B333B85FFE8A46DD884595B0A620B4EE"><span class="filepath"> /flashaccess/sync/v4</span> </li> 
     <li id="li-E4771D3C5AA5454CA1EDCFAA3E027CC1"><span class="filepath"> /flashaccess/sync/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">同期要求のURL。 このURLは、ライセンスで同期要件を指定した場合にのみアクセスできる必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-plq-ydn-44"> 
     <li id="li-81C96F93BA904C8C95B907F1A77E6494"><span class="filepath"> /flashaccess/domain/v3</span> </li> 
     <li id="li-40F0952F09674CA3B9AAFB5A62F9D02E"><span class="filepath"> /flashaccess/domain/v4</span> </li> 
     <li id="li-3ADE44B959B548F8A31A6FF08537AF46"><span class="filepath"> /flashaccess/domain/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ドメイン登録用のURL。 このURLは、ドメインサポートを実装している場合にのみアクセス可能である必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <ul id="ul-btm-c2n-44"> 
     <li id="li-3535EDF7C644406FAC471D4234C4AF98"><span class="filepath"> /flashaccess/dereg/v3</span> </li> 
     <li id="li-AB33657BC7E140E695767710DF7AEC72"><span class="filepath"> /flashaccess/dereg/v4</span> </li> 
     <li id="li-D15B32BCD4674269A3A2644DD5204707"><span class="filepath"> /flashaccess/dereg/v5</span> </li> 
    </ul> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ドメインの登録解除用のURL。 このURLは、ドメインサポートを実装している場合にのみアクセス可能である必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/headerconversion/v1/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">FMRMS 1.x DRMメタデータをAdobe Access DRMメタデータに変換するためにクライアントが使用するURL。 </p> <p class="- topic/p ">注意：このURL <i class="+ topic/ph hi-d/i ">はSSL(HTTPS)を使用する必要があります</i>。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /edcws/services/urn:EDCLicenseService/*</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">LiveCycle Rights Management ES WebサービスのURL。 コンテンツが以前のバージョンのFMRMSを使用して公開された場合、このURLを使用すると、古いクライアントがサーバーに接続し、Adobe Accessにアップグレードするように求められます。 </p> <p class="- topic/p ">注意：このURL <i class="+ topic/ph hi-d/i ">はSSL(HTTPS)を使用する必要があります</i>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "><span class="filepath"> /flashaccess/lreturn/v5</span> </td> 
   <td colname="2" class="- topic/entry "> <p>ライセンスの返却URL。 URLは、ライセンス返却サポートを実装している場合にのみアクセス可能である必要があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>内部ファイアウォールでは、リバースプロキシ経由で、上記のURLに対してのみAdobe Accessライセンスサーバーへの接続を許可する必要があります。 スケーラビリティを向上させるために、リバースプロキシとAdobe Accessの間の接続はHTTP経由で行われます。

## 送信URL {#section-FFF9F7BB353149F4A27F8788E9934A48}

ライセンスサーバーは、次のCRLをアドビからダウンロードするために、ファイアウォールを介したアクセスを必要とします。

* https://crl2.adobe.com/Adobe/FlashAccessRootCA.crl<span></span>
* https://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl<span></span>
* https://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl<span></span>
* https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl<span></span>