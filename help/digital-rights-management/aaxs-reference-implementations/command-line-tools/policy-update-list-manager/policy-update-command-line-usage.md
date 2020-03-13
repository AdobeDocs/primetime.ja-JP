---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: 1c3a450d-5d9c-4437-89dd-1bd8719268b7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# コマンドラインの使用 {#command-line-usage}

Policy Update List Managerは、DVDの\Reference Implementation\Command Line Toolsディレクトリにあります。 ポリシー更新リストを作成するには、次の構文を使用します。

```
    java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` ポリシー更新リストが書き込まれる場所を示します。

既存のポリシー更新リストを表示するには、次の構文を使用します。

```
    java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

次の表に、上記の構文に示したコマンドラインオプションの説明を示します。

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、ポリシー更新リストマネージャーは作業ディレク <span class="filepath"> トリ内でflashaccesstools.properties </span> を検索します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -dファイル名 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシー更新リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日 </span> </td> 
   <td colname="2" class="- topic/entry "> （オプション）ポリシー更新リストの有効期限。 形式は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:secです </span> （例えば、2009-01-31-14:30:00は1月31日の午後2:30を表します）。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のポリシー更新リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 </p> <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されている証明書とは異なる証明書で署名されている場合は、証明書ファイルを指定して、署名を検証できるようにします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 コピー先のファイルが既に存在し、 <span class="codeph"> -oが設 </span> 定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> date <span class="+ topic/ph pr-d/codeph codeph"> " </span> reasonCode <span class="+ topic/ph pr-d/codeph codeph"> " " </span>Reason <span class="+ topic/ph pr-d/codeph codeph"> " " reason </span>Text " reason URL <span class="+ topic/ph pr-d/codeph codeph"></span>ID " </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）指定した日付のポリシーIDを失効させます。 オプションの理由コード、理由テキストおよび理由URLも指定できます。 オプションのパラメーターに値が指定されていないことを示す空の文字列""を指定します。 日付を <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-ddまたは </span><span class="+ topic/ph pr-d/codeph codeph"></span> yyyy-mm-dd-h24:min:secと指定します（例：2008年12月1日の午前0時は2008-12-1または2008-12-00:00）。 日付が指定されていない場合は、現在の日付が使用されます。 理由コードは0以上にする必要があります。 複数の —rオプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policy </span> date " reasonCode <span class="+ topic/ph pr-d/codeph codeph"> " " </span> reason <span class="+ topic/ph pr-d/codeph codeph"> text " </span>filename " reason <span class="+ topic/ph pr-d/codeph codeph"> text " reason URL theURL </span><span class="+ topic/ph pr-d/codeph codeph"></span>name" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">-rフラグと同じアクションを実行しますが、指定したファイルからポリシー識別子を抽出します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>ライセンスリクエスト内の一致するポリシーを、特定の理由コード（オプション）、理由テキスト（オプション）および理由URL（オプション）を使用して、このポリシーで置き換えます。 </p> <p>オプションのパラメーターに値が指定されていないことを示す空の文字列""を指定します。 </p> <p>理由コードは0以上にする必要があり <span class="codeph"> ます </span>。 複数の <span class="codeph"> -uオプシ </span> ョンを指定できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

