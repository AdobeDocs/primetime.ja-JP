---
seo-title: 概要
title: 概要
uuid: 857390be-dd14-46c0-b8f7-2bc661c515d4
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# DRMライセンスジェネレーター {#license-generator}

クライアント [!DNL AdobeLicenseGenerator.jar] がライセンス要求をサーバーに送信する必要がなく、ライセンスを生成する場合に使用します。 その後、事前生成されたライセンスをコンテンツに埋め込んだり、単純なHTTP Webサーバーなどの他のメカニズムを通じてクライアントにライセンスを配信したりできます。

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

* `metadata` - Adobe Primetime DRMメタデータを含みます。

   Media Packagerのオプションを使用して、保護されたコンテンツからこのフ `-d -m` ァイルを取得することができます。

**以前に生成されたライセンスの表示：**

```
java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

* `license` - License Generatorで生成されたAdobe Primetime DRMライセンスが含まれます。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRM License Generatorは現在の作業ディレクトリ内の <span class="filepath"> flashaccesstools.properties</span> を検索します。 </p> <p>注意： コマンドラインで指定したオプションは、設定ファイルで指定したオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d licensefile#-d licensefile# <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"></span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> 生成済みのライセンスに関する情報を表示します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> リーフライセンスを生成し、出力を指定したファイルに保存します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成する必要があるコンテンツのメタデータを指定します。 このオプションは、ライセンスを生成する際に必要です。 </td> 
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
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">指定した受信者のライセンスを生成します。 デバイス証明書またはドメイン証明書を使用でき、複数の —rオプションを指定し <span class="+ topic/ph pr-d/codeph codeph"> て複数の受 </span>信者用のライセンスを作成できます。 </td> 
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
>nを含むプロパティ名 *の場合*、 *n* は1で始まり、プロパティの各インスタンスで増加する整数を表します。

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
   <td colname="2" class="- topic/entry "> <p>現在サポートされている最小クライアントバージョンを設定します。 このプロパティを設定しない場合、すべてのバージョンがデフォルトで自動的にサポートされます。 </p> <p>この値を設定すると、古いクライアントがサポートしていないライセンス要件にどのように対応するかを制御できます。 <span class="codeph"> x</span> （Adobe Primetime DRM x.0の場合）を指定します。 <span class="codeph"></span> xはメジャーリリース番号を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.keyServerCert</span> </td> 
   <td colname="2" class="- topic/entry "> キーサーバー証明書。キーサーバーで使用されるアドビ発行のライセンスサーバー証明書です。 この証明書は、iOSデバイスへのキーの配信にキーサーバーが必要であることをメタデータ/DRMポリシーが示している場合にのみ適用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certfile</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンス署名用のライセンスサーバーの資格情報を含むPKCS12ファイル。 このプロパティは、証明書と秘密鍵を含む.pfxファイルを参照する必要があります。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph"> licensegen.sign.certpass</span> </td> 
   <td colname="2" class="- topic/entry ">licensegen.sign.certfileオプションで指定したファイルを保護す <span class="+ topic/ph pr-d/codeph codeph"> るためのパスワード</span> 。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">licensegen.domainca.n</span> </td> 
   <td colname="2" class="- topic/entry "> <p>ドメインバインドライセンスを生成する場合は、1つ以上のドメインCA証明書を指定して、ライセンス発行者が信頼できるドメイン機関を示す必要があります。 </p> <p>ライセンスの受信者がドメイン証明書で、指定したドメインCAの1つが発行していない場合、ライセンスを生成できません。 このプロパティは、PEM <span class="filepath"> またはDER</span> 形式の証明書を含む.cerファイルを指定します。 <span class="codeph">nは</span> 、1から始まる単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <lines>
     <span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric licenseServerCredential.n</span>
    </lines> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">メタデータおよびDRMポリシーのCEKを復号化するための追加のライセンスサーバー資格情報を含む、オプションのPKCS12ファイル。 コンテンツがlicensegen.sign.certfileで指定された証明書以外のLicense Server証明書でパッケージ化されている場合は、追加の資格情報を設 <span class="codeph"> 定できます</span>。 このプロパティは、証明書と秘密鍵を含む <span class="filepath"> .pfx</span> (.pfx)ファイルを参照する必要があります。 <span class="codeph">nは</span> 、1から始まる単調に増加する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> 
    <lines>
     <span class="+ topic/ph pr-d/codeph codeph">licensegen.keys.asymmetric licenseServerCredential.n.password</span>
    </lines> </td> 
   <td colname="2" class="- topic/entry "> <p>パスワードは、licensegen.keys.asymmetric.licenseServerCredential.n<span class="+ topic/ph pr-d/codeph codeph"> プロパティで指定したファイルを保護するために適用されます</span> 。 </p> </td> 
  </tr> 
 </tbody> 
</table>