---
title: DRM 失効リストマネージャー
description: DRM 失効リストマネージャー
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# DRM 失効リストマネージャー {#policy-revocation-list-manager}

Primetime DRM Revocation List Manager コマンドラインツール ( [!DNL AdobeRevocationListManager.jar]) をクリックして失効リストを作成および管理し、ポリシーが失効したかどうかを確認します。

実行する前に [!DNL AdobeRevocationListManager.jar]を設定する場合は、 *Policy Update List Manager と Revocation List Manager のプロパティ* 設定ファイルのセクションに含める必要があります。

>[!NOTE]
>
>また、すべての失効リストマネージャーのプロパティをコマンドラインから指定することもできます。

## Revocation List Manager コマンドラインの使用 {#revocation-list-manager-command-line-usage}

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
* `crlNumber` 証明書失効リスト (CRL) の、負でないバージョン番号を表します。 CRL が更新されるたびに、この数値を増やす必要があります。

**表 5：コマンドラインオプション**

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
   <td colname="2" class="- topic/entry "><p class="- topic/p ">設定ファイルの名前と場所を指定します。 </p><p class="- topic/p ">名前や場所を指定しない場合、DRM 失効リストマネージャーは <span class="filepath"> flashaccesstools.properties</span> 現在の作業ディレクトリ内。 </p><p>注：コマンドラインで指定するオプションは、設定ファイルで指定するオプションよりも優先されます。 </p>設定ファイルの場所を指定します。 このオプションを適用しない場合、失効リストマネージャーは <span class="filepath"> flashaccesstools.properties</span> を作業ディレクトリに追加します。 </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-d ファイル名</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">失効リストに関する情報を表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="+ topic/ph pr-d/codeph codeph">-e 日</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">（オプション）失効リストの有効期限。 次のいずれかの形式を使用します。 
     <ul id="ul_2C89F8183C3647C593CB67576D9DED07"> 
      <li id="li_A866F6CBCB464193A119A6609C8F3B2A"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_B5F9F6C995E64464838DDE447848F707"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> </li> 
     </ul>例： 2009-01-31-14:30:00 は 1 月 31 日の午後 2 時半を表します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-f filename[certfile]</span> </td> 
   <td colname="2" class="- topic/entry "> <p>既存の失効リストからすべてのエントリを追加します。 既存のファイルは 1 つだけ指定できます。 </p> <p class="- topic/p ">既存のリストが、新しいリストへの署名に使用した資格情報以外の資格情報で署名された場合は、署名を検証するために、その証明書ファイルの横で証明書ファイルを指定する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -noprompt</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">宛先ファイルを上書きするかどうかを確認しないでください。 宛先ファイルが既に存在し、 <span class="codeph"> -o</span> が設定されていない場合、エラーが発生します。 </p> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> -o</span> </td> 
   <td colname="2" class="- topic/entry "> 宛先ファイルが既に存在する場合は、プロンプトを表示せずに上書きできます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph">-r issuerName serialNumber revocationDate</span> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">によって識別された証明書を取り消します。 <span class="codeph"> issuerName</span> および <span class="codeph"> serialNumber</span> を指定した日付に設定します。 The <span class="codeph"> issuerName</span> は 509 名前形式を使用する必要があります。 例： <span class="codeph"> CN=12345,O=Adobe Systems Incorporated,C=US</span>. </p> <p>シリアル番号は 16 進形式で指定する必要があります。 また、失効日を次のいずれかの形式で指定する必要があります。 
     <ul id="ul_1524FBC6818248F3A2B271243E649400"> 
      <li id="li_BC618EA2332D42A59B1B5434CAFFD2AF"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd</span> </li> 
      <li id="li_97F77810D20C4CF2944EFCFF5DFAE467"><span class="+ topic/ph pr-d/codeph codeph">yyyy-mm-dd-h24:min:秒</span> </li> 
     </ul>例：2008-12-1や2008-12-1-00:00:2008 年 12 月 1 日午前 0 時。 失効日を指定しない場合、現在の日付が自動的に適用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定プロパティ {#configuration-properties}

失効リストに署名するには、資格情報を適用する必要があります。 次の Revocation List Manager プロパティは、証明書のパスワードと共に、署名失効リスト (License Server Certificate) の資格情報を含む PKCS12 ファイルを指定します。

* `revocation.sign.certfile=license-server-credentials.pfx`
* `revocation.sign.certpass=password`
