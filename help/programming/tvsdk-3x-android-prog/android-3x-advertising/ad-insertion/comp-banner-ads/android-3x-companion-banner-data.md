---
description: AdAssetのコンテンツは、コンパニオンバナーを表します。
seo-description: AdAssetのコンテンツは、コンパニオンバナーを表します。
seo-title: コンパニオンバナーデータ
title: コンパニオンバナーデータ
uuid: f54aecea-5e11-45dd-97d0-5774ca631a4d
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# コンパニオンバナーデータ {#companion-banner-data}

AdAssetのコンテンツは、コンパニオンバナーを表します。

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

各レポートに `AdAsset` は、アセットの表示に関する情報が表示されます。

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <b>利用可能な情報 </b></th> 
   <th colname="col2" class="entry"> <b>説明</b> </th> 
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
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 静的URL </td> 
   <td colname="col2"> <p>コンパニオンバナーには、画像または <span class="codeph"> .swf</span><span class="codeph"></span> （フラッシュバナー）への直接URLである静的URLも含まれる場合があります。 </p> <p>htmlまたはiframeを使用しない場合は、画像またはswfへの直接URLを使用して、代わりにFlashステージにバナーを表示できます。 この場合、静的URLを使用してバ <span class="codeph"> ナーを表示</span> できます。 </p> <p>重要： 静的URLが有効な文字列であるかどうかを確認する必要があります。これは、このプロパティが常に使用可能とは限らない場合があるためです。 </p> </td> 
  </tr> 
 </tbody> 
</table>