---
seo-title: 概要
title: 概要
uuid: 857390be-dd14-46c0-b8f7-2bc661c515d4
translation-type: tm+mt
source-git-commit: d2b8cb67c54fadb8e0e7d2bdc15e393fdce8550e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# DRM License Generator {#license-generator}

ライセンス要求 [!DNL AdobeLicenseGenerator.jar] をサーバーに送信する必要がなく、ライセンスを生成する場合に使用します。 その後、事前生成されたライセンスをコンテンツに埋め込んだり、単純なHTTP Webサーバーなどの他のメカニズムを使用してクライアントにライセンスを配信したりできます。

## License Generatorコマンドラインの使用 {#license-generator-command-line-usage}

**ライセンスの生成：**

```
java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

* `metadata` -Adobe PrimetimeDRMメタデータを含みます。

   Media Packagerの `-d -m` オプションを使用して、保護されたコンテンツからこのファイルを取得できます。

**以前に生成されたライセンスの表示：**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license`  — ライセンスジェネレーターで生成されたAdobe PrimetimeDRMライセンスが含まれます。

**表6:オプション**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_skr_vry_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM License Generatorは、現在の作業ディレクトリ内で <span class="filepath"> flashaccesstools.properties</span> を検索します。 </p> <p>注意： コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> 既に生成されているライセンスに関する情報が表示されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> リーフライセンスを生成し、出力を指定されたファイルに保存します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成する必要があるコンテンツメタデータを指定します。 このオプションは、ライセンスを生成する際に必要です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、 <span class="codeph"> -o</span> が設定されていない場合は、エラーが発生します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> <p>メタデータに複数のDRMポリシーが含まれる場合は、ライセンスの生成に使用できるDRMポリシーの数を指定できます。 </p> <p>DRMポリシーの数を指定しない場合、最初のDRMポリシーが自動的に適用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r受信者証明書</span> </td> 
   <td colname="2" class="- topic/entry ">指定した受信者のライセンスを生成します。 デバイス証明書またはドメイン証明書を使用でき、複数の —r <span class="+ topic/ph pr-d/codeph codeph"></span>オプションを指定して複数の受信者用のライセンスを作成できます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ルートライセンスを生成し、出力を指定したファイルに保存します。 </td> 
  </tr> 
 </tbody> 
</table>

## 設定ファイルのプロパティ {#configuration-file-properties}

License Generatorを実行する前に、設定ファイルでLicense Generatorプロパティの値を指定する必要があります。

>[!NOTE]
>
>プロパティ名に *nが含まれる場合、* n ** は1を持つ開始を表し、プロパティの各インスタンスごとに増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> <p>現在サポートされている最小クライアントバージョンを設定します。 このプロパティを設定しない場合、デフォルトではすべてのバージョンが自動的にサポートされます。 </p> <p>この値を設定して、古いクライアントがサポートしていないライセンス要件に対してどのように対応するかを制御できます。 x <span class="codeph"> (Adobe PrimetimeDRM x.0の場合)を指定します。</span><span class="codeph"></span> xはメジャーリリース番号を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> キーサーバー証明書：キーサーバーで使用されるAdobe発行のライセンスサーバー証明書です。 この証明書は、iOSデバイスへのキーの配信にキーサーバーが必要であることがメタデータ/DRMポリシーによって示されている場合にのみ適用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスの署名に必要なライセンスサーバーの資格情報を含むPKCS12ファイルです。 このプロパティは、証明書と秘密鍵を含む.pfxファイルを参照する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">licensegen.sign.certfile <span class="+ topic/ph pr-d/codeph codeph"></span> オプションで指定したファイルを保護するためのパスワード。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>ドメインバウンドライセンスを生成する場合、1つ以上のドメインCA証明書を指定して、ライセンス発行者が信頼できるドメイン機関を示す必要があります。 </p> <p>ライセンス受信者がドメイン証明書で、指定したドメインCAの1つが発行していない場合は、ライセンスを生成できません。 このプロパティは、PEM形式またはDER形式の証明書が含まれる <span class="filepath"> .cer</span> ファイルを指定します。 <span class="codeph">nは</span> 、1から始まる単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">メタデータおよびDRMポリシーのCEKを復号化するための追加のライセンスサーバー資格情報を含む、オプションのPKCS12ファイルです。 licensegen.sign.certfileで指定された資格情報以外のLicense Server証明書がコンテンツにパッケージ化されている場合は、追加の資格情報を設定でき <span class="codeph"> ます</span>。 このプロパティは、証明書と秘密鍵を含む <span class="filepath"> .pfx</span> ファイルを参照する必要があります。 <span class="codeph">nは</span> 、1から始まる単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n.password</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p>パスワードは、licensegen.keys.asymmetric.licenseServerCredential.n<span class="+ topic/ph pr-d/codeph codeph"></span> プロパティで指定したファイルを保護するために適用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>