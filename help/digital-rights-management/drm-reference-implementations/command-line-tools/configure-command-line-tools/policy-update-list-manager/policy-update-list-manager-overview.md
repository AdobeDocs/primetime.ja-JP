---
seo-title: 概要
title: 概要
uuid: 19d05867-c210-4cd0-bc2f-5dd75f5774e5
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# DRMポリシー更新リストマネージャ{#policy-update-list-manager}

Primetime DRM Policy Update Managerコマンドラインツール([!DNL AdobePolicyUpdateListManager.jar])を使用して、DRMポリシーの更新リストを作成および管理し、ポリシーが更新されたか失効したかを確認します。

Policy Updateリストマネージャのコマンドラインツールを実行する前に、設定ファイルの&#x200B;*Policy Updateリストマネージャーと失効リストマネージャーのプロパティ*&#x200B;セクションにプロパティを設定する必要があります。

>[!NOTE]
>
>コマンドラインから、Policy Updateリストマネージャーのすべてのプロパティを指定することもできます。

## Policy Updateリストマネージャのコマンドラインの使用{#policy-update-list-manager-command-line-usage}

**ポリシー更新リストの作成：**

```
java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` drmポリシーの更新リストが書き込まれるファイルの名前を示します。

**既存のポリシー更新リストの表示:**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` ポリシー更新リストファイルの名前です。

**表4:コマンドラインオプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前または場所を指定しない場合、DRMポリシー更新リストマネージャーは、現在の作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties </span>を検索します。 </p> <p>注意： コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -dファイル名  </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRMポリシーの更新リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e日  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>（オプション）DRMポリシー更新リストの有効期限です。 </p> <p><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec </span>の形式を使用します（例えば、2009-01-31-14:30:00は1月31日の午後2時30分を表します）。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -fファイル名[certfile]  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存のDRMポリシー更新リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 </p> <p class="- topic/p ">既存のリストが、新しいリストへの署名に使用されている証明書とは異なる証明書で署名されている場合は、その証明書ファイルを指定して署名を検証する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o </span>が設定されていない場合は、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o  </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルが既に存在する場合は、確認せずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID  </span> <span class="+ topic/ph pr-d/codeph codeph"> date  </span> reasonText  <span class="+ topic/ph pr-d/codeph codeph"> " "  </span>reasonText  <span class="+ topic/ph pr-d/codeph codeph"> " "  </span>reasonURL  <span class="+ topic/ph pr-d/codeph codeph">  </span>URL " </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）指定した日付のDRMポリシーIDを失効させます。 オプションで、理由コード、理由テキストおよび理由URLを指定できます。 オプションのパラメーターに値が指定されていないことを示すには、空の文字列""を指定する必要があります。 日付は、次の形式で<span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span>または<span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:sec </span>に指定できます。 例えば、2008-12-1または2008-12-1-00:00:00は、2008年12月1日の午前0時を表します)。 日付を指定しない場合は、現在の日付が自動的に適用されます。 したがって、理由コードは0以上にする必要があります。 複数の —rオプションを指定することもできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> date </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p "><span class="codeph"> -r </span>オプションと同じ操作を実行します。 ただし、指定したファイルからDRMポリシー識別子が抽出されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL"  </span> </td> 
   <td colname="2" class="- topic/entry "> <p>特定の理由コード（オプション）、理由テキスト（オプション）および理由URL（オプション）を使用して、ライセンスリクエスト内の一致するDRMポリシーをこのDRMポリシーに置き換えます。 </p> <p>空の文字列""は、オプションのパラメーターに値が指定されていないことを示します。 </p> <p>理由コードは<span class="codeph"> 0 </span>以上にする必要があります。 複数の<span class="codeph"> -u </span>オプションを指定できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 構成プロパティ{#configuration-properties}

次のPrimetime DRM Policy Update Policy Managerプロパティでは、失効リスト(License Server Certificate)に署名するための秘密鍵証明書とパスワードを含むPKCS12ファイルを指定します。

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`