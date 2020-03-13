---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: 273e9d3b-efeb-46fa-a4b1-f13247b4e498
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コマンドラインの使用 {#command-line-usage}

失効リストマネージャーは、DVDの\Reference Implementation\Command Line Toolsディレクトリにあります。 ツールを実行するには、次のいずれかの構文を使用します。

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
* `crlNumber` は、証明書失効リスト(CRL)の非負のバージョン番号です。 この数値は、CRLが更新されるたびに増分されます。

次の表に、上記の構文に示したコマンドラインオプションの説明を示します。

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
   <td colname="2" class="- topic/entry ">設定ファイルの場所を指定します。 このオプションを使用しない場合、失効リストマネージャーは作業ディレクト <span class="filepath"> リ内でflashaccesstools.properties</span> を検索します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-dファイル名</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">失効リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e日</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）失効リストの有効期限。 形式 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> 、 <span class="+ topic/ph pr-d/codeph codeph"></span> yyyy-mm-dd-h24:min:secを使用します（例えば、2009-01-31-14:30:00は1月31日の午後2:30を表します）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry ">既存の失効リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されている証明書とは異なる証明書で署名されている場合は、次に証明書ファイルを指定し、署名を検証できるようにします。 </p> </td> 
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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">指定した日付のissuerNameと <span class="codeph"> serialNumberで識別された</span><span class="codeph"></span> 、証明書を失効させます。 issuerName <span class="codeph"> は</span> 、509の名前形式(例： <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>)に従う必要があります。 シリアル番号は16進数形式で指定します。 失効日を <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> または <span class="+ topic/ph pr-d/codeph codeph"></span>yyyy-mm-dd-h24:min:sec(例：2008-12-1、2008-12-1-00:00:00（2008年12月1日の午前0時）)と指定します。 失効日が指定されていない場合は、現在の日付が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

