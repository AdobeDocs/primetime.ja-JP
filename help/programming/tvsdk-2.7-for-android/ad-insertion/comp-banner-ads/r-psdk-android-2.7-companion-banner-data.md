---
description: AdAssetのコンテンツは、コンパニオンバナーを説明します。
seo-description: AdAssetのコンテンツは、コンパニオンバナーを説明します。
seo-title: コンパニオンバナーデータ
title: コンパニオンバナーデータ
uuid: 4a5d78e1-5abe-45a8-b50f-14f73fdcc879
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# コンパニオンバナーデータ{#companion-banner-data}

AdAssetのコンテンツは、コンパニオンバナーを説明します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

各`AdAsset`は、アセットの表示に関する情報を提供します。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 利用可能な情報 </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> コンパニオンバナーの幅（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> コンパニオンバナーの高さ（ピクセル単位）。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> リソースタイプ </td> 
   <td colname="col2">このコンパニオンバナーのリソースタイプ： 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html:データはHTMLコードです。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe:データはiframe URL(src)です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像または<span class="codeph"> .swf</span>（フラッシュバナー）への直接URLである<span class="codeph"> staticURL</span>も含まれる場合があります。 </p> <p>htmlまたはiframeを使用しない場合は、画像またはswfへのダイレクトURLを使用して、バナーをFlashステージに表示できます。 この場合、<span class="codeph"> staticURL</span>を使用してバナーを表示できます。 </p> <p>重要： 静的URLが有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用できるとは限らないからです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

