---
description: 'null'
seo-description: 'null'
seo-title: リモートキー配信のプロパティ(iOS)
title: リモートキー配信のプロパティ(iOS)
uuid: 17e1b756-d106-47a7-99ae-641190693870
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# リモートキー配信のプロパティ(iOS){#remote-key-delivery-properties-ios}

Adobe PrimetimeDRMでiOSクライアントに対するリモートキー配信のライセンス生成をサポートするには、`flashaccess-refimpl.properties`ファイルでキーサーバー証明書を指定する必要があります。

Primetime DRMに次のプロパティが追加されました。

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
   <td colname="2" class="- topic/entry "> <p>Adobeが発行するキーサーバーのライセンスサーバー証明書。 </p> <p>この証明書は、メタデータがキーサーバーが必要であることを示している場合に、iOSデバイスのライセンスを生成します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>HSMに保存されるキーサーバーのAdobe発行ライセンスサーバー証明書のエイリアス。 </p> <p>HSMを有効にする場合、<span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>プロパティの代わりに、このプロパティを適用できます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

