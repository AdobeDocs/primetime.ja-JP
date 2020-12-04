---
seo-title: 概要
title: 概要
uuid: 5487d1d3-7eb8-410d-a4b1-cde3e94c00a1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# DRMライセンス埋め込み{#license-embedder}

[!DNL AdobeLicenseEmbedder.jar]を使用して、事前に生成されたライセンスをMedia Packagerが保護するコンテンツに埋め込みます。

## ライセンス埋め込みコマンドラインの使用{#license-embedder-command-line-usage}

```
java -jar AdobeLicenseEmbedder.jar sourcefile destfile [options]
```

* `sourcefile` は、暗号化されたファイルを表します。
* `destfile` 埋め込みライセンスを含む暗号化されたコンテンツを保存するファイルの名前を指定します。

   ディレクトリを指定すると、ファイルは保存先のディレクトリに保存されます。 ソースファイルの名前も、保存先ディレクトリに保存されるファイルの名前になります。

次の表に、指定できるコマンドラインオプションを示します。

**表7:オプション**

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_hnl_2sy_n4">  
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -l license-filename  </span> </td> 
   <td colname="2" class="- topic/entry "> 埋め込むライセンスを含むファイルの名前。 複数の<span class="codeph"> -l </span>オプションを指定して、複数のライセンスを埋め込むことができます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename  </span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成できるコンテンツメタデータを指定します。 このオプションは、ライセンスを生成する際に必要です。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o </span>が適用されていない場合は、エラーが発生します。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
 </tbody> 
</table>
