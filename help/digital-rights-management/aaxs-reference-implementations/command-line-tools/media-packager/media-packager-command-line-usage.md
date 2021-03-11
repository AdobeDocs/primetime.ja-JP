---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---


# コマンドラインの使用{#command-line-usage}

Media Packagerを使用する前に、要件に記載されている要件を満たしていること、および設定ファイルに必要な情報が含まれていることを確認してください(『Adobeアクセスリファレンス導入の使用』の「設定ファイル」を参照)。**

Media Packagerは、DVDの[!DNL \Reference Implementation\Command Line tools]ディレクトリにあります。 1つのファイルを暗号化するには、次の構文を使用します。

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  source  
 <i class="+ topic ph hi-d="" i "="">
   dest [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `source` は、暗号化するファイルです。
* `dest` 暗号化されたコンテンツを書き込む場所を指定します。ディレクトリを指定した場合、暗号化されたファイルはソースファイルと同じファイル名を使用してこのフォルダーに保存されますが、ソースファイルを含むディレクトリは指定できません。

複数のファイルを同じキーで暗号化するには（マルチビットレートをサポートする場合）、次の構文を使用します。

```
java -jar AdobePackager.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefiles  
 <i class="+ topic ph hi-d="" i "="">
   dest-directory [ 
  <i class="+ topic ph hi-d="" i "="">
    options] 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

* `sourcefiles` は、暗号化するファイルを表す、空白で区切られた一連のソースエントリです。
* `dest-directory` 暗号化されたコンテンツを書き込む場所を指定します。暗号化されたファイルは、ソースファイルと同じファイル名を使用してこのフォルダーに保存されますが、ソースファイルを含むディレクトリにはできません。

暗号化されたファイルに関する表示情報を取得するには、次の構文を使用します。

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` は暗号化されたファイルです。

メタデータファイルに関する表示情報を取得するには、次の構文を使用します。

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` は、DRMメタデータを含む [!DNL .metadata] ファイルです。

>[!NOTE]
>
>パッケージ化の際、Media Packagerでデフォルトで.headerファイルが生成されなくなります。 このファイルを生成するには、パッケージ化の際に`-h`オプションを使用します。

次の表に、上の構文に示したコマンドラインオプションの説明を示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_wgz_spy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-c <span class="+ topic/ph pr-d/codeph codeph"> configfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Media Packagerは作業ディレクトリ内で<span class="filepath"> flashaccesstools.properties </span>を探します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する情報が表示されます。 ソースファイルと保存先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する情報を表示します。 ソースファイルと保存先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージファイルからポリシーを抽出するには、このオプションを<span class="codeph"> -d </span>と共に使用します。 ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名とポリシー識別子を使用して作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> -d </span>と共に使用して、パッケージファイルからDRMヘッダーを抽出します。 ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と拡張子<span class="filepath"> .header </span>を使用して作成されます </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このコンテンツの固有な識別子を指定します。 識別子が指定されていない場合は、デストファイル名が使用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph">キー</span>= <span class="+ topic/ph pr-d/codeph codeph">値</span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 複数の<span class="codeph"> -k </span>オプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">パッケージファイルからメタデータを抽出するには、<span class="codeph"> -d </span>と共にこのオプションを使用します。 ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と拡張子<span class="codeph"> .metadata </span>を使用して作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o </span>が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保存先のファイルが既に存在する場合は、確認を求めずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーを含むファイルの名前を指定します。 ポリシーで、プロパティファイルで指定されたものとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書も指定する必要があります。 </p> <p class="- topic/p ">複数の<span class="codeph"> -p </span>オプションを指定できます。クライアントはデフォルトで最初のオプションを使用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

