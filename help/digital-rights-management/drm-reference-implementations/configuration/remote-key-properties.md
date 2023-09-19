---
title: リモートキー配信プロパティ (iOS)
description: リモートキー配信プロパティ (iOS)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# リモートキー配信プロパティ (iOS){#remote-key-delivery-properties-ios}

Adobe Primetime DRM でiOSクライアントへのリモートキー配信のライセンスの生成をサポートするには、 `flashaccess-refimpl.properties` ファイル。

Primetime DRM に次のプロパティが追加されました。

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
   <td colname="2" class="- topic/entry "> <p>Adobeが発行したキーサーバーのライセンスサーバー証明書。 </p> <p>この証明書は、メタデータがキーサーバーが必要であることを示している場合に、iOSデバイスのライセンスを生成します。 </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>HSM に保存されるキーサーバーのAdobe発行ライセンスサーバー証明書のエイリアス。 </p> <p>HSM を有効にすると、 <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> プロパティ。 </p> </td> 
  </tr> 
 </tbody> 
</table>
