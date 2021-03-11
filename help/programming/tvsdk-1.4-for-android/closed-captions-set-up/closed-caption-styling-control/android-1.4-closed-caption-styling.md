---
description: TextFormatクラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 プレイヤーが表示するクローズドキャプションのスタイルを設定します。
title: クローズドキャプションのスタイル設定を制御する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# クローズドキャプションのスタイル設定を制御する{#control-closed-caption-styling-overview}

TextFormatクラスを使用して、クローズドキャプショントラックのスタイル設定情報を指定できます。 プレイヤーが表示するクローズドキャプションのスタイルを設定します。

このクラスには、フォントの種類、サイズ、色、背景の不透明度などのクローズドキャプションのスタイル情報がカプセル化されています。 関連付けられたヘルパークラス`TextFormatBuilder`は、クローズドキャプションスタイル設定の作業を容易にします。

## クローズドキャプションのスタイルを設定{#set-closed-caption-styles}

TVSDKのメソッドを使用して、クローズドキャプションテキストのスタイルを設定できます。

1. メディアプレイヤーがPREPARED状態以上になるのを待ちます。
1. `TextFormatBuilder`インスタンスを作成します。

   すべてのクローズドキャプションのスタイル設定パラメーターを指定するか、後で設定することができます。

   TVSDKは、クローズドキャプションスタイル情報を`TextFormat`インターフェイスにカプセル化します。 `TextFormatBuilder`クラスは、このインターフェイスを実装するオブジェクトを作成します。

   ```java
   public TextFormatBuilder( 
      Font font, 
      Size size, 
      FontEdge fontEdge, 
      Color fontColor, 
      Color backgroundColor, 
      Color fillColor, 
      Color edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity)
   ```

1. `TextFormat`インターフェイスを実装するオブジェクトへの参照を取得するには、`TextFormatBuilder.toTextFormat`パブリックメソッドを呼び出します。

   これは、メディアプレイヤーに適用できる`TextFormat`オブジェクトを返します。

   ```java
   public TextFormat toTextFormat()
   ```

1. 必要に応じて、次のいずれかの操作を行って、現在のクローズドキャプションスタイル設定を取得します。

   * `MediaPlayer.getCCStyle`を使用して、すべてのスタイル設定を取得します。

      戻り値は`TextFormat`インターフェイスのインスタンスです。

      ```js
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws IllegalStateException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws IllegalStateException;
      ```

   * `TextFormat` getterメソッドを使用して、設定を一度に1つずつ取得します。

      ```js
      public Color getFontColor(); 
      public Color getBackgroundColor(); 
      public Color getFillColor(); // retrieve the font fill color 
      public Color getEdgeColor(); // retrieve the font edge color 
      public Size getSize(); // retrieve the font size 
      public FontEdge getFontEdge(); // retrieve the font edge type 
      public Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity();
      ```

1. スタイル設定を変更するには、次のいずれかの操作を行います。

   >[!NOTE]
   >
   >WebVTTキャプションのサイズは変更できません。

   * setterメソッド`MediaPlayer.setCCStyle`を使用して、`TextFormat`インターフェイスのインスタンスを渡します。

      ```js
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws IllegalStateException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws IllegalStateException;
      ```

   * `TextFormatBuilder`クラスを使用します。このクラスは、個々のsetterメソッドを定義します。

      `TextFormat`インターフェイスは不変オブジェクトを定義するので、getterメソッドのみが存在し、setterメソッドは存在しません。 クローズドキャプションのスタイル設定パラメーターは、`TextFormatBuilder`クラスでのみ設定できます。

      ```js
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(Color backgroundColor) 
      public void setFillColor(Color fillColor) 
      // set the font-edge color 
      public void setEdgeColor(Color edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(Color fontColor)
      ```

クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに最大で数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション{#closed-caption-styling-options}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイル設定オプションよりも優先されます

```
public TextFormatBuilder(
 Font font,
 Size size,
 FontEdge fontEdge,
 Color fontColor,
 Color backgroundColor,
 Color fillColor,
 Color edgeColor,
 int fontOpacity,
 int backgroundOpacity,
 int fillOpacity,
 String bottomInset)
```

>[!TIP]
>
>デフォルト値（DEFAULTなど）を定義するオプションでは、キャプションが最初に指定されたときの設定を示す値が使用されます。

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> 形式 </b></th> 
   <th colname="2" class="entry"> <b>説明</b> </th> 
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
   <td colname="1"> フォントエッジ </td> 
   <td colname="2"> <p>浮き出し、なしなど、フォントエッジに使用する効果。 </p> <p><span class="codeph"> TextFormat.FontEdge </span>定義済みリストで定義されている値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p><span class="codeph"> TextFormat.Color </span>定義済みリストで定義された値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> エッジカラー </td> 
   <td colname="2"> <p>エッジ効果のカラー。 </p> <p>フォントカラーに使用できる任意の値に設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景色 </td> 
   <td colname="2"> <p>背景文字のセルの色。 </p> <p>フォントカラーに使用できる値にのみ設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りのカラー </td> 
   <td colname="2"> <p>テキストが配置されているウィンドウの背景の色。 </p> <p>フォントカラーに使用できる任意の値に設定できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントの不透明度 </td> 
   <td colname="2"> <p>テキストの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> フォント </span> のDEFAULT_OPACITYは100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 背景の不透明度 </td> 
   <td colname="2"> <p>背景文字セルの不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> 背景 </span> のDEFAULT_OPACITYは100です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> 塗りの不透明度 </td> 
   <td colname="2"> <p>キャプションウィンドウの背景の不透明度。 </p> <p>0（完全に透明）～ 100（完全に不透明）のパーセンテージで表します。 <span class="codeph"> 塗りのDEFAULT_OPACITY </span> は0です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## キャプションの書式設定の例{#examples-caption-formatting}

クローズドキャプションの形式設定を指定できます。

**例1:形式の値を明示的に指定する**

```java
private final MediaPlayer.PlaybackEventListener  
  _playbackEventListener = new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder(TextFormat.Font.DEFAULT, 
        TextFormat.Size.DEFAULT, 
        TextFormat.FontEdge.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.Color.DEFAULT, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY, 
        TextFormat.DEFAULT_OPACITY).toTextFormat(); 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

**例2:パラメーターでの形式の値の指定**

```java
/** 
* Constructor using parameters to initialize a TextFormat. 
* 
* @param font 
* The desired font. 
* @param size 
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
public TextFormatBuilder( 
    Font font, Size size, FontEdge fontEdge, 
    Color fontColor, Color backgroundColor,  
    Color fillColor, Color edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat toTextFormat(); 
 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public TextFormatBuilder setFont(Font font); 
... 
```
