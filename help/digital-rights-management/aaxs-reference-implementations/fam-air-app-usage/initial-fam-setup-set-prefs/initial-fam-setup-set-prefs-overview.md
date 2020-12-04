---
seo-title: 環境設定の概要
title: 環境設定の概要
uuid: d1c067b1-6c2b-460e-8d00-5a5bfee0789c
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# 環境設定の概要{#setting-preferences-overview}

PackagerサーバーのURLを除き、以下に指定したすべての環境設定がサーバー上の[!DNL flashaccess-refimpl-packager.properties]ファイルに保存されます。 すべての設定は、プロパティファイルで直接変更することも、AIRアプリケーションを使用して変更することもできます。 パスワードは、サーバー上のプロパティファイルに保存されると暗号化されます。 UIに暗号化されていないパスワードを入力すると、ファイルに保存される前に暗号化されます。

>[!NOTE]
>
>すべてのディレクトリとパスは、AIRアプリケーションを実行するクライアント上ではなく、packagerサーバー上のディレクトリを参照します。

ここで行った変更は、環境設定が保存されるとすぐに有効になります。 設定の問題によりPackagerスレッドが終了しない限り、サーバーを再起動する必要はありません。

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
   <td colname="1" class="- topic/entry "> Packager Server URL </td> 
   <td colname="2" class="- topic/entry "> <span class="filepath"> flashaccess-packager.war </span>；を実行しているサーバーの場所例：<span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> リソースディレクトリ </td> 
   <td colname="2" class="- topic/entry "> Packagerサーバーに必要なポリシー、証明書、秘密鍵証明書およびその他のリソースを含むディレクトリ </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> ライセンスサーバのURL </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">クライアントがライセンスを要求するサーバのURL例：<span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

