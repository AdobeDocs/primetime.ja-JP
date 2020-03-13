---
description: クローズドキャプショントラックのスタイル情報は、TextFormatクラスを使用して指定できます。このクラスは、プレイヤーが表示するクローズドキャプションのスタイルを設定します。
seo-description: クローズドキャプショントラックのスタイル情報は、TextFormatクラスを使用して指定できます。このクラスは、プレイヤーが表示するクローズドキャプションのスタイルを設定します。
seo-title: クローズドキャプションのスタイル設定の制御
title: クローズドキャプションのスタイル設定の制御
uuid: b5d9c783-755f-47a2-acb1-966df9d6116e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# クローズドキャプションのスタイル設定の制御 {#control-closed-caption-styling}

クローズドキャプショントラックのスタイル情報は、TextFormatクラスを使用して指定できます。このクラスは、プレイヤーが表示するクローズドキャプションのスタイルを設定します。

このクラスは、フォントタイプ、サイズ、色、背景の不透明度などのクローズドキャプションのスタイル情報をカプセル化します。

## クローズドキャプションのスタイルの設定 {#section_C9B5E75C70DD42E59DC4DD0F308C8216}

TVSDKのメソッドを使用して、クローズドキャプションテキストのスタイルを設定できます。

1. メディアプレイヤーが少なくともステータスになるまで待 `PREPARED` ちます。
1. インスタンスを作 `TextFormatBuilder` 成します。

   すべてのクローズドキャプションのスタイル設定パラメーターを指定するか、後で設定することができます。

   TVSDKは、クローズドキャプションのスタイル情報をインターフェイスにカプセル `TextFormat` 化します。 このインタ `TextFormatBuilder` ーフェイスを実装するオブジェクトを作成します。

   ```java
   public TextFormatBuilder( 
      TextFormat.Font font, 
      TextFormat.Size size, 
      TextFormat.FontEdge fontEdge, 
      java.lang.String fontColor, 
      java.lang.String backgroundColor, 
      java.lang.String fillColor, 
      java.lang.String edgeColor, 
      int fontOpacity, 
      int backgroundOpacity, 
      int fillOpacity 
      java.lang.String bottomInset, 
      java.lang.String safeArea)
   ```

1. インターフェイスを実装するオブジェクトへの参照を取得す `TextFormat` るには、パブリックメソッドを `TextFormatBuilder.toTextFormat` 呼び出します。

   メディアプレ `TextFormat` イヤーに適用できるオブジェクトを返します。

   `public TextFormat toTextFormat()`


1. 必要に応じて、次のいずれかの操作を行って、現在のクローズドキャプションのスタイル設定を取得します。

   * すべてのスタイル設定を取得します。戻り値 `MediaPlayer.getCCStyle` はインターフェイスのインスタンス `TextFormat` です。

      ```java
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws MediaPlayerException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws MediaPlayerException;
      ```

   * インターフェイスのgetterメソッドを使用して、設定を一度に1 `TextFormat` つずつ取得します。

      ```java
      public java.lang.String getFontColor(); 
      public java.lang.String getBackgroundColor(); 
      public java.lang.String getFillColor(); // retrieve the font fill color 
      public java.lang.String getEdgeColor(); // retrieve the font edge color 
      public TextFormat.Size getSize(); // retrieve the font size 
      public TextFormat.FontEdge getFontEdge(); // retrieve the font edge type 
      public TextFormat.Font getFont(); // retrieve the font type 
      public int getFontOpacity(); 
      public int getBackgroundOpacity(); 
      public java.lang.String getBottomInset(java.lang.String bi); 
      public java.lang.String getSafeArea(java.lang.String sa);
      ```

1. スタイル設定を変更するには、次のいずれかの操作を行います。

   * setterメソッドを使用し、イ `MediaPlayer.setCCStyle`ンターフェイスのインスタンスを渡 `TextFormat` します。

      ```java
      /** 
      * Sets the closed captioning style. Used to control the closed captioning font, 
      * size, color, edge and opacity.  
      * 
      * This method is safe to use even if the current media stream doesn't have closed 
      * captions. 
      * 
      * @param textFormat 
      * @throws MediaPlayerException 
      */ 
      public void setCCStyle(TextFormat textFormat) throws MediaPlayerException;
      ```

   * 個々のsetterメソ `TextFormatBuilder` ッドを定義するクラスを使用します。

      インターフ `TextFormat` ェイスは、getterメソッドのみでsetterメソッドがないように不変オブジェクトを定義します。 クローズドキャプションのスタイル設定パラメーターは、次のクラスでのみ設定で `TextFormatBuilder` きます。

      ```java
      // set font type 
      public void setFont(Font font)  
      public void setBackgroundColor(String backgroundColor) 
      public void setFillColor(String fillColor) 
      // set the font-edge color 
      public void setEdgeColor(String edgeColor)  
      // set the font size 
      public void setSize(Size size)  
      // set the font edge type 
      public void setFontEdge(FontEdge fontEdge)  
      public void setFontOpacity(int fontOpacity) 
      public void setBackgroundOpacity(int backgroundOpacity) 
      // set the font-fill opacity level 
      public void setFillOpacity(int fillOpacity)  
      public void setFontColor(String fontColor) 
      public void setBottomInset(String bi) 
      public void setSafeArea(String sa) 
      public void setTreatSpaceAsAlphaNum(bool)
      ```

      [!IMPORTANT]

      **カラー設定：** Android TVSDK 2.Xでは、クローズドキャプションのカラースタイルが強化されました。 この機能強化により、RGBカラー値を表す16進文字列を使用してクローズドキャプションの色を設定できます。 RGB 16進カラー表現は、Photoshopなどのアプリケーションで使い慣れた6バイトの文字列です。

          * FFFFFF = Black
          * 00000 = White
          * FF0000 = Red
          * 00FF00 = Green
          * 0000FF = Blue
      など。

      アプリケーションでは、に色のスタイル情報を渡すたびに、 `TextFormatBuilder`以前と同じように列挙を使用しますが、値を文字列として取得するには、色に `Color``getValue()` 追加する必要があります。 例：

      `tfb = tfb.setBackgroundColor(TextFormat.Color.RED      <b>.getValue()</b>);`


クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに最大で数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション {#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションより優先されます。

```java
public TextFormatBuilder( 
   Font font, 
   Size size, 
   FontEdge fontEdge, 
   String fontColor, 
   String backgroundColor, 
   String fillColor, 
   String edgeColor, 
   int fontOpacity, 
   int backgroundOpacity, 
   int fillOpacity,  
   String bottomInset 
   String safeArea)
```

>[!TIP]
>
>デフォルト値(例えば、 `DEFAULT`)を定義するオプションで、その値はキャプションが最初に指定された時の設定を示します。

<table frame="all" colsep="1" rowsep="1" id="table_87205DEFEE384AF4AF83952B15E18A42"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> 書式 </b></th> 
   <th colname="2" class="entry"> <b>説明</b> </th> 
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
   <td colname="1"> フォントエッジ </td> 
   <td colname="2"> <p>浮き出しやなしなど、フォントエッジに使用する効果。 </p> <p>TextFormat.FontEdge列挙で定義された値にのみ設定で <span class="codeph"> きま </span> す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p>TextFormat.Color列挙で定義された値にのみ設定で <span class="codeph"> きま </span> す。 </p> </td> 
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
   <td colname="2"> <p>テキストが配置されているウィンドウの背景の色。 </p> <p>フォントカラーに使用できる任意の値に設定できます。 </p> </td> 
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
  <tr rowsep="1"> 
   <td colname="1"> 下余白 </td> 
   <td colname="2"> <p>キャプションを避けるためのキャプションウィンドウの下端からの垂直方向の距離。 </p> <p>キャプションウィンドウの高さ（例：「20%」）またはピクセル数（例：「20」）の割合で表します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> セーフエリア </td> 
   <td colname="2"> <p>キャプションが表示されない、画面の端の周りの0 ～ 25 %の領域です。 </p> <p>デフォルトでは、WebVTTのセーフエリアは0%です。 この設定を使用すると、アプリケーションがデフォルトを上書きできます。 例えば、2つの値を指定する場合、文字列「10%,20%」は、最初の値が水平セーフ領域、2番目の値が垂直セーフ領域です。 1つの値（例えば「15%」という文字列）を指定した場合、垂直軸と水平軸の両方で、指定したセーフ領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## キャプションの形式設定の例 {#section_58E8E82494EC4683B010FFDE67485CF9}

クローズドキャプションの形式設定を指定する方法の例を次に示します。

```java
private final MediaPlayer.PlaybackEventListener _playbackEventListener = 
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() { 
        // Set CC style. 
        TextFormat tf = new TextFormatBuilder( 
            TextFormat.Font.DEFAULT, 
            TextFormat.Size.DEFAULT, 
            TextFormat.FontEdge.DEFAULT, 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.Color.DEFAULT.getValue(), 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY, 
            TextFormat.DEFAULT_OPACITY).toTextFormat(); 
 
        mediaPlayer.setCCStyle(tf); 
        ... 
    } 
} 
```

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
public  
<b>TextFormatBuilder</b>( 
    Font font, Size size, FontEdge fontEdge, 
    String fontColor, String backgroundColor,  
    String fillColor, String edgeColor, 
    int fontOpacity, int backgroundOpacity, 
    int fillOpacity); 
/** 
* Creates a TextFormat with the parameters supplied to this builder. 
*/ 
public TextFormat  
<b>toTextFormat</b>(); 
/** 
* Sets the text font. 
* @param font The desired font 
* @return This builder object to allow chaining calls 
*/ 
public  
<b>TextFormatBuilder</b> setFont(Font font); 
...
```

