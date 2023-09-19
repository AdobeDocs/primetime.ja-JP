---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

ライセンスを生成するには、次の構文を使用します。

```
    java -jar AdobeLicenseGenerator.jar -m 
<i class="+ topic ph hi-d="" i "="">
 metadata 
 <i class="+ topic ph hi-d="" i "="">
   [options]
 </i class="+ topic>
</i class="+ topic>
```

`metadata` は、Access の DRM メタデータを含む.metadataAdobeです。 このファイルは、 `-d -m` オプションを使用して、Media Packager にアクセスできます。

以前に生成したライセンスを表示するには、次の構文を使用します。

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` は、ライセンスジェネレータで生成されたAdobeアクセスライセンスを含むファイルです。

次の表に、前述の構文と共に指定できるコマンドラインオプションを示します。

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
   <td colname="2" class="- topic/entry "> 設定ファイルの場所を指定します。 このオプションを使用しない場合、ライセンスジェネレーターは作業ディレクトリ内で flashaccesstools.properties を探します。 コマンドラインで指定したオプションは、設定ファイルに存在するオプションよりも優先されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"> licensefile</span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> 既に生成されたライセンスに関する情報を表示します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> リーフライセンスを生成し、出力を指定したファイルに書き込みます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成するコンテンツのメタデータを指定します。 （ライセンスの生成に必要） </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o</span> が設定されていない場合は、エラーが返されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルが既に存在する場合は、確認を求めずに上書きします。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> メタデータに複数のポリシーが含まれる場合は、使用するポリシーの数（1 から始まる）を指定してライセンスを生成します。 指定しなかった場合は、最初のポリシーが使用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">指定した受信者のライセンスを生成します。 デバイスまたはドメイン証明書を使用できます。 複数 <span class="+ topic/ph pr-d/codeph codeph"> -r </span>複数の受信者用のライセンスを作成する場合は、オプションを指定できます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ルートライセンスを生成し、出力を指定したファイルに書き込みます。 </td> 
  </tr> 
 </tbody> 
</table>
