---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# DRM ライセンス埋め込み機能 {#license-embedder}

用途 [!DNL AdobeLicenseEmbedder.jar] :Media Packager が保護するコンテンツに事前に生成されたライセンスを埋め込むためのものです。

## ライセンス埋め込みコマンドラインの使用 {#license-embedder-command-line-usage}

```
java -jar AdobeLicenseEmbedder.jar sourcefile destfile [options]
```

* `sourcefile` は、暗号化されたファイルを表します。
* `destfile` 埋め込みライセンスを使用して暗号化されたコンテンツを保存するファイル名を指定します。

  ディレクトリを指定した場合、ファイルは宛先ディレクトリに保存されます。 ソースファイルの名前は、宛先ディレクトリに保存されるファイルの名前にもなります。

次の表に、指定できるコマンドラインオプションを示します。

**表 7：オプション**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_hnl_2sy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l license-filename </span> </td> 
   <td colname="2" class="- topic/entry "> 埋め込むライセンスを含むファイルの名前。 複数の <span class="codeph"> -l </span> 複数のライセンスを埋め込むためのオプション。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成できるコンテンツメタデータを指定します。 このオプションは、ライセンスを生成する際に必要です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が適用されていない場合、エラーが発生します。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
 </tbody> 
</table>
