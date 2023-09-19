---
description: AdAsset のコンテンツは、コンパニオンバナーを表します。
title: コンパニオンバナーデータ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# コンパニオンバナーデータ {#companion-banner-data}

AdAsset のコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

各 `AdAsset` には、アセットの表示に関する情報が記載されています。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 利用可能な情報 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 幅 </td> 
   <td colname="col2"> コンパニオンバナーの幅（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 高さ </td> 
   <td colname="col2"> コンパニオンバナーの高さ（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> リソースタイプ </td> 
   <td colname="col2">このコンパニオンバナーのリソースタイプ： 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html：データはHTMLコードです。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe：データは iframe URL(src) です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的 URL </td> 
   <td colname="col2"> <p>コンパニオンバナーにも <span class="codeph"> staticURL</span> 画像または <span class="codeph"> .swf</span> （Flash バナー）。 </p> <p>html や iframe を使用しない場合は、画像または swf への直接 URL を使用して、代わりにFlashステージにバナーを表示できます。 この場合、 <span class="codeph"> staticURL</span> バナーを表示します。 </p> <p>重要：静的 URL が有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用可能とは限らない場合があるからです。 </p> </td> 
  </tr> 
 </tbody> 
</table>
