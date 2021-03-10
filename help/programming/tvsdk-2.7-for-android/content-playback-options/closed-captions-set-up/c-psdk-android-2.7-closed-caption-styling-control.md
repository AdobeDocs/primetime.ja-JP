---
description: クローズドキャプショントラックのスタイル情報は、TextFormatクラスを使用して指定できます。このクラスは、プレイヤーが表示するクローズドキャプションのスタイルを設定します。
title: クローズドキャプションのスタイル設定を制御する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---


# クローズドキャプションのスタイル設定を制御する{#control-closed-caption-styling}

クローズドキャプショントラックのスタイル情報は、TextFormatクラスを使用して指定できます。このクラスは、プレイヤーが表示するクローズドキャプションのスタイルを設定します。

このクラスには、フォントの種類、サイズ、色、背景の不透明度などのクローズドキャプションのスタイル設定情報がカプセル化されます。

## クローズドキャプションのスタイルを設定{#section_C9B5E75C70DD42E59DC4DD0F308C8216}

TVSDKのメソッドを使用して、クローズドキャプションテキストのスタイルを設定できます。

1. メディアプレイヤーが`PREPARED`以上のステータスになるのを待ちます。
1. `TextFormatBuilder`インスタンスを作成します。

   すべてのクローズドキャプションのスタイル設定パラメーターを指定するか、後で設定することができます。

   TVSDKは、クローズドキャプションスタイル情報を`TextFormat`インターフェイスにカプセル化します。 `TextFormatBuilder`クラスは、このインターフェイスを実装するオブジェクトを作成します。

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

1. `TextFormat`インターフェイスを実装するオブジェクトへの参照を取得するには、`TextFormatBuilder.toTextFormat`パブリックメソッドを呼び出します。

   >[!NOTE]
   >
   >これは、メディアプレイヤーに適用できる`TextFormat`オブジェクトを返します。

   ```java
   public TextFormat toTextFormat()
   ```

1. 必要に応じて、次のいずれかの操作を行って、現在のクローズドキャプションスタイル設定を取得します。

   * `MediaPlayer.getCCStyle`ですべてのスタイル設定を取得します。戻り値は`TextFormat`インターフェイスのインスタンスです。

      ```java
      /** 
      * @return the current closed captioning style.  
      * If no style was previously set, it returns a TextFormat object 
      * with default values for each attribute. 
      * @throws MediaPlayerException if media player was already released. 
      */ 
      public TextFormat getCCStyle() throws MediaPlayerException;
      ```

   * `TextFormat` getterメソッドを使用して、設定を一度に1つずつ取得します。

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

   * setterメソッド`MediaPlayer.setCCStyle`を使用して、`TextFormat`インターフェイスのインスタンスを渡します。

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

   * `TextFormatBuilder`クラスを使用します。このクラスは、個々のsetterメソッドを定義します。

      `TextFormat`インターフェイスは不変オブジェクトを定義するので、getterメソッドのみが存在し、setterメソッドは存在しません。 クローズドキャプションのスタイル設定パラメーターは、`TextFormatBuilder`クラスでのみ設定できます。

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

      >[!IMPORTANT]
      >
      >**カラー設定：Android TVSDK 2.** Xでは、クローズドキャプションのカラースタイルが強化されました。この機能強化により、RGBカラー値を表す16進文字列を使用してクローズドキャプションの色を設定できるようになりました。 RGB 16進数カラー表現は、Photoshopなどのアプリケーションで使用する、使い慣れた6バイトの文字列です。
      >
      >* FFFFFF =黒
      >* 000000 =白
      >* FF0000 =赤
      >* 00FF00 =緑
      >* 0000FF =青

      >
      >など。
      >
      >アプリケーションでは、色スタイル情報を`TextFormatBuilder`に渡す場合は常に、以前と同じように`Color`定義済みリストを使用しますが、ここで、値を文字列として取得するには、色に`getValue()`を追加する必要があります。 例：
      >
      >
      ```
      >tfb = tfb.setBackgroundColor(TextFormat.Color.RED <b>.getValue()</b>);
      >```




クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに最大で数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション{#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイル設定オプションよりも優先されます。

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
  <tr rowsep="1"> 
   <td colname="1"> 下の差込枠 </td> 
   <td colname="2"> <p>キャプションが表示されないようにする、キャプションウィンドウの下端からの垂直方向の距離。 </p> <p>キャプションウィンドウの高さに対する割合（「20%」など）またはピクセル数（「20」など）で表します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> セーフエリア </td> 
   <td colname="2"> <p>画面の端の周囲の0 ～ 25 %の領域で、キャプションが表示されません。 </p> <p>デフォルトでは、WebVTTの安全領域は0 %です。 この設定を使用すると、アプリケーションがそのデフォルト設定を上書きできます。 例えば、文字列「10%,20%」のように2つの値を指定した場合、1つ目の値は水平方向のセーフ領域、2つ目の値は垂直方向のセーフ領域になります。 1つの値を指定する場合（例えば文字列「15%」）、垂直軸と水平軸の両方で、指定したセーフ領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## キャプションの書式設定の例{#section_58E8E82494EC4683B010FFDE67485CF9}

クローズドキャプションの形式設定を指定する方法の例を以下に示します。

**例1:形式の値を明示的に指定する**

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
