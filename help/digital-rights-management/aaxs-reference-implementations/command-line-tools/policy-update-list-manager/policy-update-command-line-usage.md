---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

ポリシー更新リストマネージャーは、DVD の\参照実装\コマンドラインツールディレクトリにあります。 ポリシー更新リストを作成するには、次の構文を使用します。

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` ポリシー更新リストの書き込み先を示します。

既存のポリシー更新リストを表示するには、次の構文を使用します。

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

次の表に、上記の構文に示すコマンドラインオプションの説明を示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、Policy Update List Manager は <span class="filepath"> flashaccesstools.properties </span> を作業ディレクトリに追加します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d ファイル名 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシー更新リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e 日 </span> </td> 
   <td colname="2" class="- topic/entry "> （オプション）ポリシー更新リストの有効期限。 形式を使用 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> ( 例：2009-01-31-14:30:00 は 1 月 31 日（午後 2 時 30 分）を表します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のポリシー更新リストからすべてのエントリを追加します。 既存のファイルを 1 つだけ指定できます。 </p> <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されたものとは異なる資格情報で署名されている場合は、証明書ファイルを指定して、署名を検証できるようにします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルが既に存在する場合は、確認を求めずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> 日付 </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）指定した日付にポリシー ID を取り消します。 オプションの理由コード、理由テキストおよび理由 URL も指定できます。 空の文字列""を指定して、オプションのパラメーターに値が指定されていないことを示します。 日付を次のように指定します。 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> ( 例：2008-12-1または2008-12-1-00:00:00（2008 年 12 月 1 日午前 0 時）。 日付が指定されていない場合は、現在の日付が使用されます。 理由コードは 0 以上である必要があります。 複数の —r オプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> 日付 </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">-r フラグと同じ処理を実行しますが、指定されたファイルからポリシー識別子を抽出します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>指定された理由コード（オプション）、理由テキスト（オプション）、理由 URL（オプション）を使用して、ライセンスリクエスト内の一致するポリシーをこのポリシーに置き換えます。 </p> <p>空の文字列""を指定して、オプションのパラメーターに値が指定されていないことを示します。 </p> <p>理由コードは次の値以上である必要があります <span class="codeph"> 0 </span>. 複数 <span class="codeph"> -u </span> オプションを指定できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
