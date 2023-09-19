---
title: 環境設定の概要
description: 環境設定の概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# 環境設定の概要 {#setting-preferences-overview}

Packager Server URL を除き、以下に指定するすべての環境設定は、 [!DNL flashaccess-refimpl-packager.properties] ファイルをサーバー上に置きます。 すべての設定は、プロパティファイルで直接変更することも、AIRアプリケーションを使用して変更することもできます。 パスワードは、サーバー上の properties ファイルに保存されると暗号化されます。 UI に暗号化されていないパスワードを入力します。パスワードは暗号化されてから、ファイルに保存されます。

>[!NOTE]
>
>すべてのディレクトリとパスは、AIRアプリケーションを実行するクライアント上ではなく、Packager サーバー上のディレクトリを参照します。

ここで行った変更は、環境設定が保存されるとすぐに有効になります。 設定の問題が原因で Packager スレッドが終了しない限り、サーバーを再起動する必要はありません。

環境設定の説明では、次の用語を使用します。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> 環境設定 </th> 
   <th colname="2" class="- topic/entry entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Packager サーバー URL </td> 
   <td colname="2" class="- topic/entry "> 実行中のサーバーの場所 <span class="filepath"> flashaccess-packager.war </span>例： <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> リソースディレクトリ </td> 
   <td colname="2" class="- topic/entry "> Packager サーバーに必要なポリシー、証明書、資格情報、およびその他のリソースを含むディレクトリ </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> ライセンスサーバー URL </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントがライセンスを要求するサーバーの URL。例： <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>
