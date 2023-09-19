---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

失効リストマネージャーは、DVD の\参照実装\コマンドラインツールディレクトリにあります。 ツールを実行するには、次のいずれかの構文を使用します。

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
* `crlNumber` は、証明書失効リスト (CRL) の負でないバージョン番号です。 この数値は、CRL が更新されるたびに増加する必要があります。

次の表に、上記の構文に示すコマンドラインオプションの説明を示します。

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
   <td colname="2" class="- topic/entry ">設定ファイルの場所を指定します。 このオプションを使用しない場合、失効リストマネージャーは <span class="filepath"> flashaccesstools.properties</span> を作業ディレクトリに追加します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d ファイル名</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">失効リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e 日</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）失効リストの有効期限。 形式を使用 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> または <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> ( 例：2009-01-31-14:30:00 は 1 月 31 日（午後 2 時 30 分）を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">既存の失効リストからすべてのエントリを追加します。 既存のファイルを 1 つだけ指定できます。 <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されたものとは異なる資格情報で署名されている場合は、次に証明書ファイルを指定して、署名を検証できるようにします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、-o が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルが既に存在する場合は、確認を求めずに上書きします。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">次の条件で識別された証明書を失効させます： <span class="codeph"> issuerName</span> および <span class="codeph"> serialNumber</span> を指定した日付に設定します。 The <span class="codeph"> issuerName</span> は、509 名前フォーマット ( 例： <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>) をクリックします。 16 進数形式でシリアル番号を指定します。 失効日の指定： <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> または <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span>例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 失効日が指定されていない場合は、現在の日付が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
