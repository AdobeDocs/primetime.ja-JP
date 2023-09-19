---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---

# DRM ポリシー更新リストマネージャー {#policy-update-list-manager}

Primetime DRM Policy Update List Manager コマンドラインツール ( [!DNL AdobePolicyUpdateListManager.jar]) を使用して、DRM ポリシーの更新リストを作成および管理したり、ポリシーが更新されたか取り消されたかを確認したりできます。

Policy Update List Manager コマンドラインツールを実行する前に、 *Policy Update List Manager と Revocation List Manager のプロパティ* 設定ファイルのセクションに含める必要があります。

>[!NOTE]
>
>また、すべてのポリシー更新リストマネージャーのプロパティをコマンドラインから指定することもできます。

## Policy Update List Manager のコマンドラインの使用 {#policy-update-list-manager-command-line-usage}

**ポリシー更新リストを作成します。**

```
java -jar AdobePolicyUpdateListManager.jar  
<i class="+ topic ph hi-d="" i "="">
  destfile [ 
 <i class="+ topic ph hi-d="" i "="">
   options]  
 </i class="+ topic> 
</i class="+ topic>
```

* `destfile` DRM ポリシーの更新リストが書き込まれるファイルの名前を示します。

**既存のポリシー更新リストを表示します。**

```
java -jar AdobePolicyUpdateListManager.jar -d  
<i class="+ topic ph hi-d="" i "="">
  filename 
</i class="+ topic>
```

* `filename` ポリシー更新リストファイルの名前です。

**表 4：コマンドラインオプション**

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
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p> <p class="- topic/p ">名前や場所を指定しない場合、DRM ポリシー更新リストマネージャーは <span class="filepath"> flashaccesstools.properties </span> 現在の作業ディレクトリ内。 </p> <p>注：コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p "> <span class="+ topic/ph pr-d/codeph codeph"> -d ファイル名 </span> </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">DRM ポリシーの更新リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -e 日 </span> </td> 
   <td colname="2" class="- topic/entry "> <p>（オプション）DRM ポリシーの更新リストの有効期限。 </p> <p>形式を使用 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> ( 例：2009-01-31-14:30:00 は 1 月 31 日（午後 2 時 30 分）を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -f filename [certfile] </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">既存の DRM ポリシー更新リストからすべてのエントリを追加します。 既存のファイルは 1 つだけ指定できます。 </p> <p class="- topic/p ">既存のリストが、新しいリストへの署名に使用される資格情報以外の資格情報で署名されている場合は、証明書ファイルを指定して署名を検証する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -noprompt </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o </span> が設定されていない場合、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -o </span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルが既に存在する場合は、確認を求めずに上書きします。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="+ topic/ph pr-d/codeph codeph"> -r policyID </span> <span class="+ topic/ph pr-d/codeph codeph"> 日付 </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）指定した日付に DRM ポリシー ID を無効にします。 オプションで、理由コード、理由テキストおよび理由 URL を指定できます。 オプションのパラメーターに値が指定されていないことを示すために、空の文字列""を指定する必要があります。 日付は、 <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd </span> または <span class="+ topic/ph pr-d/codeph codeph"> yyyy-mm-dd-h24:min:秒 </span> の形式を変更しました。 例：2008-12-1や2008-12-1-00:00:00 は、2008 年 12 月 1 日午前 0 時を表します )。 日付を指定しない場合、現在の日付が自動的に適用されます。 したがって、理由コードは 0 以上にする必要があります。 複数の —r オプションを指定することもできます。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">-rf <span class="+ topic/ph pr-d/codeph codeph"> policyFilename </span> <span class="+ topic/ph pr-d/codeph codeph"> 日付 </span> " <span class="+ topic/ph pr-d/codeph codeph"> reasonCode </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonText </span>" " <span class="+ topic/ph pr-d/codeph codeph"> reasonURL </span>" </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">と同じアクションを実行します。 <span class="codeph"> -r </span> オプション。 ただし、指定したファイルから DRM ポリシー識別子が抽出されます。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> <span class="codeph"> -u policyFilename " reasonCode" " reasonText" " reasonURL" </span> </td> 
   <td colname="2" class="- topic/entry "> <p>ライセンスリクエスト内の一致する DRM ポリシーを、指定された理由コード（オプション）、理由テキスト（オプション）、理由 URL（オプション）を使用して、この DRM ポリシーに置き換えます。 </p> <p>空の文字列""は、オプションのパラメーターに値が指定されていないことを示します。 </p> <p>理由コードは次の値以上である必要があります <span class="codeph"> 0 </span>. 複数の <span class="codeph"> -u </span> オプション。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定プロパティ {#configuration-properties}

次の Primetime DRM Policy Update List Manager プロパティは、パスワードと共に失効リスト（ライセンスサーバー証明書）に署名するための資格情報を含む PKCS12 ファイルを指定します。

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
