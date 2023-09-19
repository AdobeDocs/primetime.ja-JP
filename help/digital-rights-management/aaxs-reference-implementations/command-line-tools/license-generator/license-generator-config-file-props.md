---
title: 設定ファイルのプロパティ
description: 設定ファイルのプロパティ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# 設定ファイルのプロパティ {#configuration-file-properties}

ライセンスジェネレータを実行する前に、ライセンスジェネレータのプロパティの値を指定します。 設定ファイルで、次のプロパティを指定します。 次を含むプロパティ名の場合： *n*, *n* は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_qk1_rry_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> プロパティ </th> 
   <th colname="2" class="- topic/entry entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.minClientVersion</span> </td> 
   <td colname="2" class="- topic/entry "> サポートされるクライアントの最小バージョンを設定します。 設定しない場合、デフォルトでは、すべてのバージョンがサポートされます。 この値を設定して、古いクライアントがサポートしていないライセンス要件に対してどのように応答するかを制御します。 x (Adobeアクセス x.0 の場合 ) を指定します。x はメジャーリリース番号です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> キーサーバー証明書 ( キーサーバーで使用されるAdobe発行のライセンスサーバー証明書 )。 この証明書は、iOSデバイスへのキー配信にキーサーバーが必要であることをメタデータ/ポリシーが示している場合にのみ使用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンス署名用のライセンスサーバー資格情報を含む PKCS12 ファイル。 このプロパティは、証明書と秘密鍵を含む.pfx ファイルを参照する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">指定したファイルの保護に使用するパスワード <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile.</span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> ドメインバインドライセンスを生成する場合は、1 つ以上のドメイン CA 証明書を指定して、このライセンス発行者によって信頼されたドメイン機関を示す必要があります。 ライセンス受信者がドメイン証明書で、指定したドメイン CA のいずれかによって発行されていない場合、ライセンスを生成できません。 このプロパティは、証明書のみを含む.cer ファイルを指定します（PEM または DER 形式が使用可能）。 n は、1 から始まり、単調に増加する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">メタデータとポリシーの CEK を復号化するための追加のライセンスサーバー資格情報を含む、オプションの PKCS12 ファイル。 コンテンツが、次で指定された以外のライセンスサーバー証明書を使用して以前にパッケージ化された場合は、追加の資格情報を設定できます。 <span class="codeph"> licensegen.sign.certfile</span>. このプロパティは、 <span class="filepath"> .pfx</span> 証明書と秘密鍵を含むファイル。 n は、1 から始まり、単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">次の方法で指定したファイルの保護に使用するパスワード： <p><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>
