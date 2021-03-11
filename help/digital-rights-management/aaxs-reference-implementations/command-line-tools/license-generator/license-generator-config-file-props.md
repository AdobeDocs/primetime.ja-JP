---
title: 設定ファイルのプロパティ
description: 設定ファイルのプロパティ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# 構成ファイルのプロパティ{#configuration-file-properties}

License Generatorを実行する前に、License Generatorプロパティの値を指定します。 設定ファイルでは、次のプロパティを指定します。 *n*&#x200B;を含むプロパティ名の場合、*n*&#x200B;は、1から始まり、プロパティの各インスタンスの増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> サポートされるクライアントの最小バージョンを設定します。 設定しなかった場合、デフォルトでは、すべてのバージョンがサポートされます。 この値を設定して、古いクライアントがサポートしていないライセンス要件にどのように対応するかを制御します。 x(Adobeアクセスx.0の場合)を指定します。xはメジャーリリース番号です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> キーサーバー証明書(キーサーバーで使用されるAdobe発行のライセンスサーバー証明書)。 この証明書は、iOSデバイスへのキーの配信にキーサーバーが必要であることをメタデータ/ポリシーが示している場合にのみ使用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンス署名用のライセンスサーバー資格情報が含まれているPKCS12ファイルです。 このプロパティは、証明書と秘密鍵を含む.pfxファイルを参照する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile.</span>で指定されたファイルの保護に使用されるパスワードです。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> ドメインバウンドライセンスを生成する場合は、1つ以上のドメインCA証明書を指定して、このライセンス発行者が信頼するドメイン機関を示す必要があります。 ライセンス受信者がドメイン証明書で、指定したドメインCAの1つが発行していない場合は、ライセンスを生成できません。 このプロパティは、証明書のみを含む.cerファイルを指定します（PEM形式またはDER形式を使用できます）。 nは、1から始まる単調に増加する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">メタデータとポリシーのCEKを復号化するための追加のライセンスサーバー資格情報を含むPKCS12ファイル（オプション）。 <span class="codeph"> licensegen.sign.certfile</span>で指定された証明書以外のLicense Server証明書がコンテンツのパッケージ化済みである場合は、追加の資格情報を設定できます。 このプロパティは、証明書と秘密鍵を含む<span class="filepath"> .pfx</span>ファイルを参照する必要があります。 nは、1から始まる単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric.licenseServerCredential.n.password</span> </td> 
   <td colname="2" class="- topic/entry ">指定したファイルの保護に使用するパスワード： <p><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> </p> </td> 
  </tr> 
 </tbody> 
</table>

