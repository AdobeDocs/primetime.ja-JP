---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: 5f24f18d-09ef-400a-9404-50a9fcf4316d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コマンドラインの使用 {#command-line-usage}

Media Packagerを使用する前に、要件に記載されている要件を満たし、必要な情報が設定ファイルに含まれていることを確認します(『Adobe Access Referenceの実装の使用』の「設定フ *ァイル」を参照してください*。

Media Packagerは、DVD上のディレ [!DNL \Reference Implementation\Command Line tools] クトリにあります。 単一のファイルを暗号化するには、次の構文を使用します。

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
* `dest` 暗号化されたコンテンツを書き込む場所を指定します。 ディレクトリを指定した場合、暗号化されたファイルはソースファイルと同じファイル名でこのフォルダーに保存されますが、ソースファイルを含むディレクトリは指定できません。

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

* `sourcefiles` は、暗号化するファイルを表す空白で区切られた一連のソースエントリです。
* `dest-directory` 暗号化されたコンテンツを書き込む場所を指定します。 暗号化されたファイルは、ソースファイルと同じファイル名を使用してこのフォルダーに保存されますが、ソースファイルを含むディレクトリではないディレクトリにする必要があります。

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

* `metadatafile` は、DRMメタデ [!DNL .metadata] ータを含むファイルです。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>パッケージ化中に、Media Packagerでデフォルトで.headerファイルが生成されなくなります。 このファイルを生成するには、パッケージ化の際にこ `-h` のオプションを使用します。

次の表に、上記の構文に示したコマンドラインオプションの説明を示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Media Packagerは作業ディレクトリ内の <span class="filepath"> flashaccesstools.properties </span> を検索します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-d encryptedfile- <span class="+ topic/ph pr-d/codeph codeph"> d encryptedfile </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既にパッケージ化されているファイルに関する情報を表示します。 ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-dmメタデータフ <span class="+ topic/ph pr-d/codeph codeph"> ァイル </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のメタデータに関する情報を表示します。 ソースファイルと宛先ファイルは不要です。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-e </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを — <span class="codeph"> dと共に使用し </span> て、パッケージファイルからポリシーを抽出します。 ファイル名とポリシー識別子を使用して、暗号化されたファイルと同じディレクトリにファイルが作成されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-h </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">-dと共に使用 <span class="codeph"> して、パッ </span> ケージファイルからDRMヘッダーを抽出します。 ファイルは、暗号化されたファイルと同じディレクトリに、ファイル名と拡張子 <span class="filepath"> .headerを使用して作成されます。 </span> </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-i <span class="+ topic/ph pr-d/codeph codeph"> contentID </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このコンテンツの一意の識別子を指定します。 識別子が指定されていない場合は、destfileファイル名が使用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-kキ <span class="+ topic/ph pr-d/codeph codeph"> ー </span>= <span class="+ topic/ph pr-d/codeph codeph"> 値 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コンテンツメタデータに追加するカスタムキー/値を指定します。 複数の <span class="codeph"> -kオプシ </span> ョンを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-m </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">このオプションを <span class="codeph"> -dと共に使用し </span> て、パッケージファイルからメタデータを抽出します。 ファイル名と拡張子.metadataを使用して、暗号化されたファイルと同じディレクトリにファイルが作成さ <span class="codeph"> れま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-noprompt </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、 <span class="codeph"> -oが設 </span> 定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-o </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">保存先のファイルが既に存在する場合は、確認メッセージを表示せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-p <span class="+ topic/ph pr-d/codeph codeph"> filename [domain-transport-cert] </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシーを含むファイルの名前を指定します。 ポリシーで、プロパティファイルで指定されたものとは異なるトランスポート証明書を使用するサーバーとのドメイン登録が必要な場合は、ドメイントランスポート証明書も指定する必要があります。 </p> <p class="- topic/p ">複数の <span class="codeph"> -pオ </span> プションを指定でき、クライアントはデフォルトで最初のオプションを使用します。 コマンドラインで指定した値は、設定ファイルで指定した値よりも優先されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

