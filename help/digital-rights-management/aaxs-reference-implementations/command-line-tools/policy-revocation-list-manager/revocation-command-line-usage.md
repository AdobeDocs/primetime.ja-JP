---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# コマンドラインの使用{#command-line-usage}

失効リストマネージャーは、DVDの\Reference Implementation\Command Line Toolsディレクトリにあります。 ツールを実行するには、次の構文のいずれかを使用します。

```
    java -jar AdobeRevocationListManager.jar 
<i class="+ topic ph hi-d="" i "="">
 destfile 
 <i class="+ topic ph hi-d="" i "="">
  crlNumber [
  <i class="+ topic ph hi-d="" i "="">
   options] 
       java -jar AdobeRevocationListManager.jar -d 
   <i class="+ topic ph hi-d="" i "="">
     filename
   </i class="+ topic>
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* `destfile` 失効リストが書き込まれる場所を示します。
* `crlNumber` は、証明書失効リスト(CRL)の負ではないバージョン番号です。この番号は、CRLが更新されるたびに増加します。

次の表に、上の構文に示したコマンドラインオプションの説明を示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_a3y_wqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> コマンドラインオプション </th> 
   <th colname="2" class="- topic/entry entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-c configfile</span> </td> 
   <td colname="2" class="- topic/entry ">設定ファイルの場所を指定します。 このオプションを使用しない場合、失効リストマネージャーは、作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties</span>を探します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-dファイル名</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">失効リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e日</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）失効リストの有効期限。 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span>または<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span>の形式を使用します（例えば、2009-01-31-14:30:00は1月31日の午後2時30分を表します）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">既存の失効リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されているものとは異なる証明書で署名されている場合は、次に証明書ファイルを指定すると、署名を検証できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、-oが設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">指定した日付に<span class="codeph"> issuerName</span>および<span class="codeph"> serialNumber</span>で識別された証明書を失効させます。 <span class="codeph"> issuerName</span>は、509名の形式に従う必要があります(例：<span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>)。 シリアル番号は16進数形式で指定します。 失効日を<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span>または<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span>として指定します（例：2008-12-1または2008-12-1-00:00）。2001年12月1日の午前0時08. 失効日が指定されていない場合は、現在の日付が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

