---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# DRM License Generator {#license-generator}

用途 [!DNL AdobeLicenseGenerator.jar] クライアントがサーバにライセンス要求を送信する必要がなく、ライセンスを生成する。 その後、事前に生成されたライセンスをコンテンツに埋め込んだり、単純な HTTP Web サーバーなどの他のメカニズムを通じてクライアントにライセンスを配信したりできます。

## License Generator コマンドラインの使用 {#license-generator-command-line-usage}

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

* `metadata` - Adobe Primetime DRM メタデータを含めます。

  このファイルを保護されたコンテンツから取得するには、 `-d -m` オプションを使用して、Media Packager を起動します。

**以前に生成したライセンスを表示する：**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license`  — ライセンスジェネレーターで生成されたAdobe Primetime DRM ライセンスが含まれます。

**表 6：オプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前や場所を指定しない場合、DRM License Generator は <span class="filepath"> flashaccesstools.properties</span> 現在の作業ディレクトリ内。 </p> <p>注：コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> 生成済みのライセンスに関する情報が表示されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> リーフライセンスを生成し、出力を指定したファイルに保存します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスの生成に必要なコンテンツメタデータを指定します。 このオプションは、ライセンスを生成する際に必要です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o</span> が設定されていない場合は、エラーが発生します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> <p>メタデータに複数の DRM ポリシーが含まれる場合は、ライセンスの生成に使用できる DRM ポリシーの数を指定できます。 </p> <p>DRM ポリシーの数を指定しない場合、最初の DRM ポリシーが自動的に適用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">指定された受信者のライセンスを生成します。 デバイスまたはドメインの証明書を使用でき、複数の <span class="+ topic/ph pr-d/codeph codeph"> -r </span>複数の受信者用のライセンスを作成するオプション。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ルートライセンスを生成し、出力を指定したファイルに保存します。 </td> 
  </tr> 
 </tbody> 
</table>

## 設定ファイルのプロパティ {#configuration-file-properties}

ライセンスジェネレータを実行する前に、設定ファイルで License Generator プロパティの値を指定する必要があります。

>[!NOTE]
>
>次を含むプロパティ名の場合： *n*, *n* は、プロパティの各インスタンスに対して 1 から始まり増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> <p>現在サポートされている最小クライアントバージョンを設定します。 このプロパティを設定しない場合、すべてのバージョンがデフォルトで自動的にサポートされます。 </p> <p>この値を設定して、古いクライアントがサポートしていないライセンス要件に対してどのように応答するかを制御できます。 指定 <span class="codeph"> x</span> (Adobe Primetime DRM x.0 の場合 ) <span class="codeph"> x</span> はメジャーリリース番号を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> Key Server Certificate：キーサーバーで使用される、Adobe発行のライセンスサーバー証明書です。 この証明書は、iOSデバイスへのキー配信にキーサーバーが必要であることがメタデータ/DRM ポリシーによって示されている場合にのみ適用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンス署名用のライセンスサーバー資格情報を含む PKCS12 ファイル。 このプロパティは、証明書と秘密鍵を含む.pfx ファイルを参照する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">で指定したファイルを保護するパスワード <span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> オプション。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>ドメインバインドライセンスを生成する場合は、1 つ以上のドメイン CA 証明書を指定して、ライセンス発行者が信頼できるドメイン機関を示す必要があります。 </p> <p>ライセンス受信者がドメイン証明書で、指定したドメイン CA のいずれかによって発行されていない場合、ライセンスを生成できません。 このプロパティは、 <span class="filepath"> .cer</span> PEM または DER 形式の証明書を含むファイル。 <span class="codeph">n</span> は、1 から始まり、単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">メタデータと DRM ポリシーの CEK を復号化するための追加のライセンスサーバー資格情報を含む、オプションの PKCS12 ファイル。 以前に、で指定された資格情報以外のライセンスサーバー証明書でコンテンツがパッケージ化されている場合は、追加の資格情報を設定できます。 <span class="codeph"> licensegen.sign.certfile</span>. このプロパティは、 <span class="filepath"> .pfx</span> 証明書と秘密鍵を含むファイル。 <span class="codeph">n</span> は、1 から始まり、単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <code>licensegen.keys.asymmetric. licenseServerCredential.n.password</code>
   </td> 
   <td colname="2" class="- topic/entry "> <p>パスワードは、<span class="+ topic/ph pr-d/codeph codeph"> licensegen.keys.asymmetric.licenseServerCredential.n</span> プロパティ。 </p> </td> 
  </tr> 
 </tbody> 
</table>
