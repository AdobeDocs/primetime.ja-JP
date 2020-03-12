---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: b3a995de-653e-491a-9262-86dc56b9ce31
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

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

`metadata` は、Adobe Access DRMメタデータを含む.metadataファイルです。 このファイルは、Media Packagerのオプションを使用して、保護されたコンテ `-d -m` ンツから取得できます。

以前に生成されたライセンスを表示するには、次の構文を使用します。

```
    java -jar AdobeLicenseGenerator.jar -d 
<i class="+ topic ph hi-d="" i "="">
  license
</i class="+ topic>
```

`license` は、License Generatorで生成されたAdobe Accessライセンスを含むファイルです。

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
   <td colname="2" class="- topic/entry "> 設定ファイルの場所を指定します。 このオプションを使用しない場合、License Generatorは作業ディレクトリ内のflashaccesstools.propertiesを検索します。 コマンドラインで指定したオプションは、設定ファイル内のオプションよりも優先されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d licensefile#-d licensefile# <i class="+ topic/ph hi-d/i "><span class="+ topic/ph pr-d/codeph codeph"></span></i> </p> </td> 
   <td colname="2" class="- topic/entry "> 既に生成されたライセンスに関する情報を表示します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-leaf-leaf-filename</span> </td> 
   <td colname="2" class="- topic/entry "> リーフライセンスを生成し、出力を指定したファイルに書き込みます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-m metadata-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成するコンテンツメタデータを指定します。 （ライセンスの生成に必要） </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、 <span class="codeph"> -o</span> が設定されていない場合は、エラーが返されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-policy policy-num</span> </td> 
   <td colname="2" class="- topic/entry "> メタデータに複数のポリシーが含まれる場合は、ライセンスの生成に使用するポリシーの番号（1から始まる）を指定します。 指定しなかった場合、最初のポリシーが使用されます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-r recipient-cert</span> </td> 
   <td colname="2" class="- topic/entry ">指定した受信者のライセンスを生成します。 デバイス証明書またはドメイン証明書を使用できます。 複数の受 <span class="+ topic/ph pr-d/codeph codeph"> 信者のラ </span>イセンスを作成する場合は、-rオプションを複数指定できます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-root root-filename</span> </td> 
   <td colname="2" class="- topic/entry "> ルートライセンスを生成し、出力を指定したファイルに書き込みます。 </td> 
  </tr> 
 </tbody> 
</table>

