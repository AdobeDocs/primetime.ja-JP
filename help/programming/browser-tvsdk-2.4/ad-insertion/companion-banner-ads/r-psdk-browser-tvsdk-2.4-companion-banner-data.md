---
description: AdBannerAssetのコンテンツは、コンパニオンバナーを表します。
seo-description: AdBannerAssetのコンテンツは、コンパニオンバナーを表します。
seo-title: コンパニオンバナーデータ
title: コンパニオンバナーデータ
uuid: b2c709da-9d19-49d1-8116-9c947371b77c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# コンパニオンバナーデータ{#companion-banner-data}

AdBannerAssetのコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

このイベ `AdobePSDK.PSDKEventType.AD_STARTED` ントは、プ `Ad` ロパティ( `companionAssets` )を含むインス `Array<AdBannerAsset>`タンスを返します。
各レポートに `AdBannerAsset` は、アセットの表示に関する情報が表示されます。

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
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html:データはHTMLコードで表されます。 </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe:データはiframe URL(src)です。 </li> 
     <li id="li_48E74AC5F00640EC8A4DE2CB31E106EC">static:データは静的な画像URL(src)です。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">
    <ph>
      バナーデータ
    </ph> </td> 
   <td colname="col2"> このコンパニオンバナーのresourceTypeで指定され <span class="codeph"> るタイプ</span> のデータです。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像への直接URLであるstaticURLが含まれる場合もあります。 </p> <p>htmlやiframeを使用しない場合は、画像への直接URLを使用できます。 この場合、staticURLを使用してバナーを表示できます。 </p> <p>重要： 静的URLが有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用可能とは限らない場合があるためです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

