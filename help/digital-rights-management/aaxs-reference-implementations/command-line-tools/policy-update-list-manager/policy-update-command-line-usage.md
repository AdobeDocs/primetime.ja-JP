---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---


# コマンドラインの使用{#command-line-usage}

ポリシー更新リストマネージャーは、DVDの\Reference Implementation\Command Line Toolsディレクトリにあります。 ポリシー更新リストを作成するには、次の構文を使用します。

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

次の表に、上の構文に示したコマンドラインオプションの説明を示します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_ghb_jqy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">コマンドラインオプション </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -c configfile  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの場所を指定します。 このオプションを使用しない場合、ポリシー更新リストマネージャーは、作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties </span>を探します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -dファイル名  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">ポリシー更新リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日  </span> </td> 
   <td colname="2" class="- topic/entry "> （オプション）ポリシー更新リストの有効期限です。 <span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec </span>の形式を使用します（例えば、2009-01-31-14:30:00は1月31日の午後2時30分を表します）。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -fファイル名[certfile]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のポリシー更新リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 </p> <p class="- topic/p ">この既存のリストが、新しいリストへの署名に使用されているものとは異なる証明書を使用して署名されている場合は、証明書ファイルを指定すると、署名を検証できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o </span>が設定されていない場合は、エラーが返されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID  </span> <span class="+ topic/ph pr-d/codeph codeph"> date  </span> reasonText  <span class="+ topic/ph pr-d/codeph codeph"> " "  </span>reasonText  <span class="+ topic/ph pr-d/codeph codeph"> " "  </span>reasonURL  <span class="+ topic/ph pr-d/codeph codeph">  </span>URL " </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）指定した日付のポリシーIDを失効させます。 オプションで、理由コード、理由テキストおよび理由URLも指定できます。 オプションのパラメーターに値が指定されていないことを示す空の文字列""を指定します。 日付を<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec </span>に指定します（例：2008-12-1または2008-12-1-00:00）。12月1日の午前0時は00:008)。 日付が指定されていない場合は、現在の日付が使用されます。 理由コードは0以上にする必要があります。 複数の —rオプションを指定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">-rフラグと同じアクションを実行しますが、指定したファイルからポリシー識別子を抽出します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL"  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>指定された理由コード（オプション）、理由テキスト（オプション）および理由URL（オプション）を使用して、ライセンスリクエスト内の一致するポリシーをこのポリシーに置き換えます。 </p> <p>オプションのパラメーターに値が指定されていないことを示す空の文字列""を指定します。 </p> <p>理由コードは<span class="codeph"> 0 </span>以上にする必要があります。 複数の<span class="codeph"> -u </span>オプションを指定できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

