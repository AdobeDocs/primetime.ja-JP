---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

Media Packager を使用する前に、要件に記載されている要件を満たしていることと、設定ファイルに必要な情報が含まれていることを確認してください ( *Adobeアクセス参照実装の使用*.

Media Packager は、 [!DNL \Reference Implementation\Command Line tools] DVD 上のディレクトリ。 単一のファイルを暗号化するには、次の構文を使用します。

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
* `dest` 暗号化されたコンテンツを書き込む場所を指定します。 ディレクトリを指定した場合、暗号化されたファイルはソースファイルと同じファイル名でこのフォルダーに保存されますが、ソースファイルを含むディレクトリをディレクトリにすることはできません。

複数のファイルを同じキーで暗号化する（マルチビットレートをサポートする）には、次の構文を使用します。

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
* `dest-directory` 暗号化されたコンテンツを書き込む場所を指定します。 暗号化されたファイルは、ソースファイルと同じファイル名を使用してこのフォルダーに保存されますが、ソースファイルを含むディレクトリをディレクトリにすることはできません。

暗号化されたファイルに関する情報を表示するには、次の構文を使用します。

```
java -jar AdobePackager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  encryptedfile [-e] [-m] 
</i class="+ topic>
```

* `encryptedfile` は、暗号化されたファイルです。

メタデータファイルに関する情報を表示するには、次の構文を使用します。

```
java -jar AdobePackager.jar -dm <metadatafile> [-e]
```

* `metadatafile` は [!DNL .metadata] DRM メタデータを含むファイル。

>[!NOTE]
>
>パッケージ化の際、Media Packager はデフォルトで.header ファイルを生成しなくなります。 このファイルを生成するには、 `-h` オプションを選択します。

次の表に、上記の構文に示すコマンドラインオプションの説明を示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Media Packager は <span class="filepath"> flashaccesstools.properties </span> を作業ディレクトリに追加します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d <span class="+ topic/ph pr-d/codeph codeph"> encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する情報を表示します。 ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dm <span class="+ topic/ph pr-d/codeph codeph"> metadatafile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する情報を表示します。 ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -d </span> パッケージ化されたファイルからポリシーを抽出する。 ファイルは、ファイル名とポリシーの識別子を使用して、暗号化されたファイルと同じディレクトリに作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">と共に使用 <span class="codeph"> -d </span> を使用して、パッケージ化されたファイルから DRM ヘッダーを抽出します。 ファイルは、ファイル名と拡張子を使用して、暗号化されたファイルと同じディレクトリに作成されます <span class="filepath"> .header </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このコンテンツの一意の識別子を指定します。 識別子が指定されていない場合は、宛先ファイルの名前が使用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-k <span class="+ topic/ph pr-d/codeph codeph"> key </span>= <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 複数 <span class="codeph"> -k </span> オプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -d </span> パッケージ化されたファイルからメタデータを抽出する。 ファイルは、ファイル名と拡張子を使用して、暗号化されたファイルと同じディレクトリに作成されます <span class="codeph"> .metadata </span>. </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既に存在する場合は、確認を求めずに宛先ファイルを上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーを含むファイルの名前を指定します。 ポリシーで、プロパティファイルで指定されたものとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書も指定する必要があります。 </p> <p class="- topic/p ">複数 <span class="codeph"> -p </span> オプションを指定でき、クライアントはデフォルトで最初のを使用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
