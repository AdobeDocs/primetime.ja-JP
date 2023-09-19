---
title: ライセンスサーバーのプロパティファイル
description: ライセンスサーバーのプロパティファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# ライセンスサーバーのプロパティファイル {#license-server-properties-file}

以下を使用します。 [!DNL flashaccess-refimpl.properties] ファイルを使用して、参照実装の License Server コンポーネントを設定します。 少なくとも、トランスポート秘密鍵証明書とライセンスサーバー秘密鍵証明書に関連するプロパティを設定してください。 秘密鍵証明書ファイルの場所は、 `config.resourcesDirectory` プロパティ。 このファイルには、コンテンツのパッケージ化に関連するプロパティも含まれています。これらのプロパティは、FlashMediaRights ManagementServer 1.x のメタデータ変換にのみ使用されます。 このプロパティファイルの値を変更した場合、変更を有効にするには、ライセンスサーバーを再起動する必要があります。

AdobeアクセスでiOSクライアントへのリモートキー配信のライセンスの生成をサポートするには、キーサーバー証明書を [!DNL flashaccess-refimpl.properties].

Adobeアクセスに次のプロパティが追加されました。

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_xz2_lwy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">プロパティ </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">説明 </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> </td> 
   <td colname="2" class="- topic/entry "> キーサーバーのライセンスサーバー証明書 (Adobe発行 )。 この証明書は、メタデータがキーサーバーが必要であることを示している場合に、iOSデバイスのライセンスを生成するために使用されます。 </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">HSM に保存されるキーサーバーのAdobe発行ライセンスサーバー証明書のエイリアス。 HSM が有効な場合は、 <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>
