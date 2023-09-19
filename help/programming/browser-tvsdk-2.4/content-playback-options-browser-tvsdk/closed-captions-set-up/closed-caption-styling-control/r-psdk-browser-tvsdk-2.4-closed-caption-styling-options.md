---
description: 複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションよりも優先されます。
title: クローズドキャプションのスタイル設定オプション
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# クローズドキャプションのスタイル設定オプション{#closed-caption-styling-options}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションよりも優先されます。

```js
new TextFormat( 
   font,  
   fontColor,  
   edgeColor,  
   fontEdge,  
   backgroundColor,  
   fillColor,  
   size,  
   fontOpacity,  
   backgroundOpacity,  
   fillOpacity, 
   bottomInset, 
   safeArea) 
```

>[!TIP]
>
>デフォルト値を定義するオプション ( 例： `DEFAULT`) の値は、キャプションが最初に指定されたときの設定を示します。

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 形式 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> フォント </td> 
   <td colname="2"> <p>フォントタイプ。 </p> <p>は、 <span class="codeph"> TextFormat.Font </span> 列挙およびは、例えば、serifs のある場合もない場合も等幅で表します。 </p> <p>ヒント：デバイス上で使用できる実際のフォントは異なる場合があり、必要に応じて置換が使用されます。 serifs を持つ Monospace は通常、代替として使用されますが、この代替はシステム固有の場合もあります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> サイズ </td> 
   <td colname="2"> <p>キャプションのサイズ。 </p> <p> は、 <span class="codeph"> TextFormat.Size </span> 列挙： 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> 中 </span>  — 標準サイズ </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> 大 </span>  — 中より約 30%大きい </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> 小 </span>  — 中より約 30%小さい </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> デフォルト </span>  — キャプションのデフォルトサイズ（中） </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p>は、 <span class="codeph"> TextFormat.Color </span> 列挙。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0 （完全な透明）～ 100 （完全な不透明）のパーセンテージで表されます。 <span class="codeph"> DEFAULT_OPACITY </span> の場合、フォントは 100 です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 下のインセット </td> 
   <td colname="2"> <p>キャプションウィンドウの下端からの、避ける垂直方向の距離。 </p> <p>キャプションウィンドウの高さに対する割合（「20%」など）またはピクセル数（「20」など）で表します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 安全な領域 </td> 
   <td colname="2"> <p>画面の端の周りの 0%～25%（キャプションは表示されない）の領域。 </p> <p>デフォルトでは、608/708の安全領域は 12%、WebVTT の安全領域は 0%です。 この設定を使用すると、アプリケーションがそのデフォルトを上書きできます。 2 つの値（例えば、文字列「10%,20%」）を指定した場合、最初の値は水平方向のセーフエリア、2 番目の値は垂直方向のセーフエリアになります。 1 つの値（文字列「15%」など）を指定した場合、垂直軸と水平軸の両方で、指定した安全な領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>
