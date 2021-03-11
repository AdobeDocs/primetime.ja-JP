---
description: 複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイル設定オプションよりも優先されます。
title: クローズドキャプションのスタイル設定オプション
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# クローズドキャプションのスタイル設定オプション{#closed-caption-styling-options}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイル設定オプションよりも優先されます。

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
>デフォルト値（例：`DEFAULT`）を定義するオプションでは、その値はキャプションが最初に指定されたときの設定を示します。

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
   <td colname="2"> <p>フォントタイプ。 </p> <p><span class="codeph"> TextFormat.Font </span>定義済みリストで定義され、例えばserifsのある（またはない）等幅を表す値にのみ設定できます。 </p> <p>ヒント： デバイスで使用できる実際のフォントは異なる場合があり、必要に応じて代替フォントが使用されます。 serifsを持つ等幅スペースは、通常、代替として使用されますが、システム固有の置換である場合もあります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> サイズ </td> 
   <td colname="2"> <p>キャプションのサイズ。 </p> <p> <span class="codeph"> TextFormat.Size </span>定義済みリストで定義された値にのみ設定できます。 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM  </span>  — 標準サイズ </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> LARGE  </span>  — 標準サイズより約30%大きい </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> SMALL  </span>  — 標準サイズより約30%小さい </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT  </span>  — キャプションのデフォルトサイズ。媒体と同じ </li> 
     </ul> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p><span class="codeph"> TextFormat.Color </span>定義済みリストで定義された値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> フォント </span> のDEFAULT_OPACITYは100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 下の差込枠 </td> 
   <td colname="2"> <p>キャプションが表示されないようにする、キャプションウィンドウの下端からの垂直方向の距離。 </p> <p>キャプションウィンドウの高さに対する割合（「20%」など）またはピクセル数（「20」など）で表します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> セーフエリア </td> 
   <td colname="2"> <p>画面の端の周囲の0 ～ 25 %の領域で、キャプションが表示されません。 </p> <p>デフォルトでは、608/708のセーフエリアは12%、WebVTTのセーフエリアは0%です。 この設定を使用すると、アプリケーションがそのデフォルト設定を上書きできます。 例えば、文字列「10%,20%」のように2つの値を指定した場合、1つ目の値は水平方向のセーフ領域、2つ目の値は垂直方向のセーフ領域になります。 1つの値を指定する場合（例えば文字列「15%」）、垂直軸と水平軸の両方で、指定したセーフ領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

