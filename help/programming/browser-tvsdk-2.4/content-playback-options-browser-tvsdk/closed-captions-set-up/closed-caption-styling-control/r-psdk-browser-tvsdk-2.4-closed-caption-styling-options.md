---
description: 複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションより優先されます。
seo-description: 複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションより優先されます。
seo-title: クローズドキャプションのスタイル設定オプション
title: クローズドキャプションのスタイル設定オプション
uuid: 0e2fd9f3-e569-4b5d-9b78-86f8ee6230ee
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# クローズドキャプションのスタイル設定オプション{#closed-caption-styling-options}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションより優先されます。

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
>デフォルト値(例えば、 `DEFAULT`)を定義するオプションで、その値はキャプションが最初に指定された時の設定を示します。

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 書式 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> フォント </td> 
   <td colname="2"> <p>フォントタイプ。 </p> <p>TextFormat.Font列挙で定義され、例えば、シリーフの有無に関わらず等 <span class="codeph"> 幅 </span> のモノスペースを表す値にのみ設定できます。 </p> <p>ヒント： デバイスで使用できる実際のフォントは異なる場合があり、必要に応じて置換が使用されます。 serifsを持つ等幅スペースは、通常、システム固有の置き換えですが、代わりに使用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> サイズ </td> 
   <td colname="2"> <p>キャプションのサイズ。 </p> <p> TextFormat.Size列挙で定義された値にのみ設定 <span class="codeph"> できま </span> す。 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> — 標準サイズ </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> LARGE </span> — 中より約30%大きい </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> SMALL </span> — 中より約30%小さい </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT </span> — キャプションのデフォルトサイズ。媒体と同じ </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p>TextFormat.Color列挙で定義された値にのみ設定で <span class="codeph"> きま </span> す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> フォントのDEFAULT_OPACITY </span> は100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 下の差込枠 </td> 
   <td colname="2"> <p>キャプションを避けるためのキャプションウィンドウの下端からの垂直方向の距離。 </p> <p>キャプションウィンドウの高さ（例：「20%」）またはピクセル数（例：「20」）の割合で表します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> セーフエリア </td> 
   <td colname="2"> <p>キャプションが表示されない、画面の端の周りの0 ～ 25 %の領域です。 </p> <p>デフォルトでは、608/708のセーフエリアは12%、WebVTTのセーフエリアは0%です。 この設定を使用すると、アプリケーションがデフォルトを上書きできます。 例えば、2つの値を指定する場合、文字列「10%,20%」は、最初の値が水平セーフ領域、2番目の値が垂直セーフ領域です。 1つの値（例えば「15%」という文字列）を指定した場合、垂直軸と水平軸の両方で、指定したセーフ領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

