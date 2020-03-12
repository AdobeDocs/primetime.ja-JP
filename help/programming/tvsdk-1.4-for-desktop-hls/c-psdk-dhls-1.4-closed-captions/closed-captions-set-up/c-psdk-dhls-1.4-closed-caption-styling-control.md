---
description: ClosedCaptionStylesクラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 これにより、プレイヤーが表示するクローズドキャプションのスタイルが設定されます。
seo-description: ClosedCaptionStylesクラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 これにより、プレイヤーが表示するクローズドキャプションのスタイルが設定されます。
seo-title: クローズドキャプションのスタイル設定の制御
title: クローズドキャプションのスタイル設定の制御
uuid: 506c06d3-8fe0-46c9-9ed6-5b35d21c021c
translation-type: tm+mt
source-git-commit: b67a9dcb0abb07f4fdff4e03d9d6c0b07ff45127

---


# クローズドキャプションのスタイル設定の制御{#control-closed-caption-styling}

ClosedCaptionStylesクラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 これにより、プレイヤーが表示するクローズドキャプションのスタイルが設定されます。

このクラスは、フォントタイプ、サイズ、色、背景の不透明度などのクローズドキャプションのスタイル情報をカプセル化します。 関連付けられたヘルパークラス `ClosedCaptionStylesBuilder`は、クローズドキャプションスタイルの設定の操作を容易にします。

## クローズドキャプションのスタイルの設定 {#section_DAE84659D1964DB1B518F91B59AF29D9}

TVSDKのメソッドを使用して、クローズドキャプションテキストのスタイルを設定できます。

1. MediaPlayerが少なくともPREPAREDステータスになるまで待ちます(有効な状態 [を待つを参照](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-ui-configure/t-psdk-dhls-1.4-ui-state-prepared-wait-for.md))。
1. スタイル設定を変更するには、次のいずれかの操作を行います。

   * ヘルパーク `ClosedCaptionStylesBuilder` ラスを使用します(背後で `ClosedCaptionStyles` 動作します)。
   * クラスを直接 `ClosedCaptionStyles` 使用します。

>[!NOTE]
>
>クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに最長で数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション {#section_D28F50B98C0D48CF89C4FB6DC81C5185}

クラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定で `ClosedCaptionStyles` きます。 これにより、プレイヤーが表示するクローズドキャプションのスタイルが設定されます。

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
   <td colname="2"> <p>フォントタイプ。 </p> <p>ClosedCaptionStyles.FONT配列で定義され、例えばシリーフのある等幅モ <span class="codeph"> ノスペースを表 </span> す値にのみ設定できます。 
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
     </code> </p> <p>ヒント： デバイスで使用できる実際のフォントは異なる場合があり、必要に応じて置換が使用されます。 serifsを持つ等幅スペースは、通常、システム固有の置き換えですが、代わりに使用されます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> サイズ </td> 
   <td colname="2"> <p>キャプションのサイズ。 </p> <p> ClosedCaptionStyles.FONT_SIZE配列で定義された値にのみ設 <span class="codeph"> 定でき </span> ます。 
     <ul compact="yes" id="ul_544BFC7A46474A74839477108F1AB1E9"> 
      <li id="li_A592ED46B8DF4D8FAD7AF3BD931A712B"> <span class="codeph"> MEDIUM </span> — 標準サイズ </li> 
      <li id="li_4F8CEDE54965430EB707DD3D5B2E3F87"> <span class="codeph"> LARGE </span> — 中より約30%大きい </li> 
      <li id="li_D78D823883F54D869118BAB58257E377"> <span class="codeph"> SMALL </span> — 中より約30%小さい </li> 
      <li id="li_9299C13408584A38835F8D91BD048083"> <span class="codeph"> DEFAULT </span> — キャプションのデフォルトサイズ。媒体と同じ </li> 
     </ul> </p> <p>ヒント： WebVTTキャプションのフォントサイズを変更するには、DefaultMediaPlayer.ccStylesセッター関数のサイズパラメ <span class="codeph"> ーターを変更 </span> します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントエッジ </td> 
   <td colname="2"> <p>浮き出しやなしなど、フォントエッジに使用する効果。 </p> <p>ClosedCaptionStyles.FONT_EDGE配列で定義された値にのみ設定で <span class="codeph"> きま </span> す。 
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
   <td colname="2"> <p>フォントの色。 </p> <p>ClosedCaptionStyles.COLOR配列で定義された値にのみ設定で <span class="codeph"> きま </span> す。 
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
   <td colname="2"> <p>エッジ効果のカラー。 </p> <p>フォントカラーに使用できる任意の値に設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りつぶしの色 </td> 
   <td colname="2"> <p>テキストが配置されているウィンドウの背景の色。 </p> <p>フォントカラーに使用できる任意の値に設定できます。 </p> <p>重要： WebVTTではこの機能が使用されないので、WebVTTキャプションには適用されません。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> フォントのDEFAULT_OPACITY </span> は100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景の不透明度 </td> 
   <td colname="2"> <p>背景文字セルの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> 背景のDEFAULT_OPACITY </span> は100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りの不透明度 </td> 
   <td colname="2"> <p>キャプションウィンドウの背景の不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> 塗りのDEFAULT_OPACITY </span> は0です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 例：キャプションの形式設定 {#section_63E33840B7A14D26990046E2ACF2ECA1}

クローズドキャプションの形式設定を指定できます。

## 例1:形式の値を明示的に指定する {#section_BD7B48F3B66D4E9290E1CB2F464E08E4}

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

## 例2:パラメーターの形式値の指定 {#section_147036D7C31C4010A5A7DF49997014A9}

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
