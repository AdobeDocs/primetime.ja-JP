---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: 72117619-a723-49d3-9aa9-5eefcf5b0916
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コマンドラインの使用 {#command-line-usage}

ライセンスを埋め込むには、次の構文を使用します。

```
    java -jar AdobeLicenseEmbedder.jar  
<i class="+ topic ph hi-d="" i "="">
  sourcefile destfile [options] 
</i class="+ topic>
```

* `sourcefile` は、暗号化されたFLVまたはF4Vファイルです。
* `destfile` 埋め込みライセンスを含む暗号化されたコンテンツを書き込む場所を指定します。 ディレクトリを指定した場合、ファイルはソースファイルと同じファイル名でこのディレクトリに保存されますが、ソースファイルを含むディレクトリは指定できません。

次の表に、前述の構文と共に指定できるコマンドラインオプションを示します。

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
   <td colname="2" class="- topic/entry "> 埋め込むライセンスを含むファイルの名前。 複数の —l <span class="codeph"> オプション </span> を指定して、複数のライセンスを埋め込むことができます。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -m metadata-filename </span> </td> 
   <td colname="2" class="- topic/entry "> ライセンスを生成するコンテンツメタデータを指定します。 （ライセンスの生成に必要） </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、 <span class="codeph"> -oが設 </span> 定されていない場合は、エラーが返されます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </td> 
  </tr> 
 </tbody> 
</table>

