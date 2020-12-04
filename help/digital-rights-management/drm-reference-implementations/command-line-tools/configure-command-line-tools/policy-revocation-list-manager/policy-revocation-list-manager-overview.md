---
seo-title: DRM失効リストマネージャー
title: DRM失効リストマネージャー
uuid: 30ab5f54-4aac-4535-b30c-b4e5dbfbc475
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---


# DRM失効リストマネージャー{#policy-revocation-list-manager}

Primetime DRM失効リストマネージャーのコマンドラインツール([!DNL AdobeRevocationListManager.jar])を使用して失効リストを作成および管理し、ポリシーが失効したかどうかを確認します。

[!DNL AdobeRevocationListManager.jar]を実行する前に、設定ファイルの&#x200B;*Policy Updateリストマネージャーと失効リストマネージャーのプロパティ*&#x200B;セクションにプロパティを設定する必要があります。

>[!NOTE]
>
>コマンドラインからすべての失効リストマネージャーのプロパティを指定することもできます。

## 失効リストマネージャのコマンドラインの使用{#revocation-list-manager-command-line-usage}

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

* `destfile` 失効リストのプロパティを保存するファイルの名前を指定します。
* `crlNumber` 証明書失効リスト(CRL)のバージョン番号を負の値以外で表します。CRLが更新されるたびに、この数値を増やす必要があります。

**表5:コマンドラインオプション**

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p><p class="- topic/p ">名前または場所を指定しない場合、DRM失効リストマネージャーは、現在の作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties</span>を検索します。 </p><p>注意： コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p>設定ファイルの場所を指定します。 このオプションを適用しない場合、失効リストマネージャーは作業ディレクトリ内の<span class="filepath"> flashaccesstools.properties</span>を検索します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-dファイル名</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">失効リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e日</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）失効リストの有効期限。 次のいずれかの形式を使用します。 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> </li> 
     </ul>例えば、2009-01-31-14:30:00は、1月31日の午後2時30分を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>既存の失効リストからすべてのエントリを追加します。 既存のファイルは1つだけ指定できます。 </p> <p class="- topic/p ">既存のリストが、新しいリストへの署名に使用した資格情報以外の資格情報で署名された場合は、署名を検証するために、その証明書ファイルを指定する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">コピー先のファイルを上書きするかどうかを確認しない。 宛先ファイルが既に存在し、<span class="codeph"> -o</span>が設定されていない場合は、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> コピー先のファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">指定した日付に<span class="codeph"> issuerName</span>および<span class="codeph"> serialNumber</span>で識別された証明書を失効させます。 <span class="codeph"> issuerName</span>は509名の形式を使用する必要があります。 例えば、<span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>とします。 </p> <p>シリアル番号は16進数形式で指定する必要があります。 また、次のいずれかの形式で失効日を指定する必要があります。 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:sec</span> </li> 
     </ul>例えば、2008年12月1日の午前0時は、2008-12-1または2008-12-1-00:00:00と指定します。 失効日を指定しない場合、現在の日付が自動的に適用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 構成プロパティ{#configuration-properties}

失効リストに署名するには、資格情報を適用する必要があります。 次のRevocation Server Managerプロパティは、証明書のパスワードと共に、失効リスト(License Server Certificate)に署名するための秘密鍵証明書が含まれるPKCS12ファイルを指定します。

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`