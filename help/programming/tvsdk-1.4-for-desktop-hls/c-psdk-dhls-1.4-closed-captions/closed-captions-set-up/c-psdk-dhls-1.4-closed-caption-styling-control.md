---
description: ClosedCaptionStyles クラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 プレーヤーで表示されるクローズドキャプションのスタイルを設定します。
title: クローズドキャプションのスタイル設定を制御する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# クローズドキャプションのスタイル設定を制御する{#control-closed-caption-styling}

ClosedCaptionStyles クラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 プレーヤーで表示されるクローズドキャプションのスタイルを設定します。

このクラスは、フォントタイプ、サイズ、色、背景の不透明度など、クローズドキャプションのスタイル設定情報をカプセル化します。 関連付けられたヘルパークラス `ClosedCaptionStylesBuilder`を使用すると、クローズドキャプションスタイルの設定を容易におこなうことができます。

## クローズドキャプションのスタイルの設定 {#section_DAE84659D1964DB1B518F91B59AF29D9}

TVSDK メソッドを使用して、クローズドキャプションのテキストのスタイルを設定できます。

1. MediaPlayer のステータスが PREPARED 以上になるまで待ちます ( [有効な状態になるのを待つ](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md)) をクリックします。
1. スタイル設定を変更するには、次のいずれかの操作を行います。

   * 以下を使用します。 `ClosedCaptionStylesBuilder` ヘルパークラス ( `ClosedCaptionStyles` ) の背後に。
   * 以下を使用します。 `ClosedCaptionStyles` クラスを直接使用します。

>[!NOTE]
>
>クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに最大で数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション {#section_D28F50B98C0D48CF89C4FB6DC81C5185}

クローズドキャプショントラックのスタイル設定情報は、 `ClosedCaptionStyles` クラス。 プレーヤーで表示されるクローズドキャプションのスタイルを設定します。

```
public function TextFormat( 
   font:String = default,  
   size:String = default,  
   fontEdge:String = default,  
   fontColor:String = default,  
   backgroundColor:String = default,  
   fillColor:String = default,  
   edgeColor:String = default,  
   fontOpacity:int,  
   backgroundOpacity:int,  
   fillOpacity:int)
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
   <td colname="2"> <p>フォントタイプ。 </p> <p>は、 <span class="codeph"> ClosedCaptionStyles.FONT </span> 配列およびは、たとえば、serifs のあるかどうかを表します。 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;AVCaptionStyle.MONOSPACE_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.MONOSPACED_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITH_SERIFS, 
      &nbsp;AVCaptionStyle.PROPORTIONAL_WITHOUT_SERIFS, 
      &nbsp;AVCaptionStyle.CASUAL, 
      &nbsp;AVCaptionStyle.CURSIVE, 
      &nbsp;AVCaptionStyle.SMALL_CAPITALS 
      &nbsp;]; 
     </code> </p> <p>ヒント：デバイス上で使用できる実際のフォントは異なる場合があり、必要に応じて置換が使用されます。 serifs を持つ Monospace は通常、代替として使用されますが、この代替はシステム固有の場合もあります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> サイズ </td> 
   <td colname="2"> <p>キャプションのサイズ。 </p> <p> は、 <span class="codeph"> ClosedCaptionStyles.FONT_SIZE </span> 配列： 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> 中 </span>  — 標準サイズ </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> 大 </span>  — 中より約 30%大きい </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> 小 </span>  — 中より約 30%小さい </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> デフォルト </span>  — キャプションのデフォルトサイズ（中） </li> 
     </ul> </p> <p>ヒント： WebVTT キャプションのフォントサイズは、 <span class="codeph"> DefaultMediaPlayer.ccStyles setter </span> 関数に置き換えます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントエッジ </td> 
   <td colname="2"> <p>フォントの端に使用する効果（浮き出し、なしなど）。 </p> <p>は、 <span class="codeph"> ClosedCaptionStyles.FONT_EDGE </span> 配列。 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;FONT_EDGE&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.NONE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RAISED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEPRESSED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.UNIFORM, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.LEFT_DROP_SHADOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RIGHT_DROP_SHADOW 
      &nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p>は、 <span class="codeph"> ClosedCaptionStyles.COLOR </span> 配列。 
     <code class="syntax actionscript">
       public&nbsp;static&nbsp;const&nbsp;COLOR&nbsp;:Array&nbsp;=&nbsp;[ 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DEFAULT, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLACK, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GRAY, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_WHITE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_RED, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_GREEN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_BLUE, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_YELLOW, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_MAGENTA, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.DARK_CYAN, 
      &nbsp;&nbsp;&nbsp;&nbsp;AVCaptionStyle.BRIGHT_CYAN&nbsp;&nbsp;&nbsp;]; 
     </code> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> エッジの色 </td> 
   <td colname="2"> <p>エッジ効果の色。 </p> <p>には、フォントカラーに使用できる任意の値を設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りの色 </td> 
   <td colname="2"> <p>テキストが配置されているウィンドウの背景の色。 </p> <p>には、フォントカラーに使用できる任意の値を設定できます。 </p> <p>重要： WebVTT はこの機能を使用しないので、これは WebVTT キャプションには適用されません。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0 （完全な透明）～ 100 （完全な不透明）のパーセンテージで表されます。 <span class="codeph"> DEFAULT_OPACITY </span> の場合、フォントは 100 です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景の不透明度 </td> 
   <td colname="2"> <p>背景文字セルの不透明度。 </p> <p>0 （完全な透明）～ 100 （完全な不透明）のパーセンテージで表されます。 <span class="codeph"> DEFAULT_OPACITY </span> の場合、背景は 100 です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りの不透明度 </td> 
   <td colname="2"> <p>キャプションウィンドウの背景の不透明度。 </p> <p>0 （完全な透明）～ 100 （完全な不透明）のパーセンテージで表されます。 <span class="codeph"> DEFAULT_OPACITY </span> の値は 0 です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 例：キャプションの書式設定 {#section_63E33840B7A14D26990046E2ACF2ECA1}

クローズドキャプションの書式設定を指定できます。

## 例 1：形式の値を明示的に指定する {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

```
private function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    var formatBuilder:TextFormatBuilder = new TextFormatBuilder(); 
    formatBuilder.font = Font.DEFAULT,  
    formatBuilder.fontSize = FontSize.DEFAULT,  
    formatBuilder.fontEdge = FontEdge.DEFAULT,  
    formatBuilder.fontColor = Color.DEFAULT,  
    formatBuilder.backgroundColor = Color.DEFAULT,  
    formatBuilder.fillColor = Color.DEFAULT,  
    formatBuilder.edgeColor = Color.DEFAULT,  
    formatBuilder.fontOpacity = .DEFAULT_OPACITY,  
    formatBuilder.backgroundOpacity = Font.DEFAULT_OPACITY,  
    formatBuilder.fillOpacity = TextFormat.DEFAULT_OPACITY 
    mediaPlayer.set CCStyle(formatBuilder.toTextFormat()); 
} 
```

## 例 2：パラメーターで形式の値を指定する {#section_147036D7C31C4010A5A7DF49997014A9}

```
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param fontSize 
* The desired text size. 
* @param fontEdge 
* The desired font edge. 
* @param fontColor 
* The desired font color. 
* @param backgroundColor 
* The desired background color. 
* @param fillColor 
* The desired fill color. 
* @param edgeColor 
* The desired color to draw the text edges. 
* @param fontOpacity 
* The desired font opacity. 
* @param backgroundOpacity 
* The desired background opacity. 
* @param fillOpacity 
* The desired fill opacity. 
*/ 
public function TextFormatBuilder(font:Font, fontSize:FontSize, fontEdge:FontEdge,  
                                  fontColor:Color, backgroundColor:Color,  
                                  fillColor:Color, edgeColor:Color, fontOpacity:int, 
                                  backgroundOpacity:int, fillOpacity:int); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public function toTextFormat():TextFormat; 
... 
```
