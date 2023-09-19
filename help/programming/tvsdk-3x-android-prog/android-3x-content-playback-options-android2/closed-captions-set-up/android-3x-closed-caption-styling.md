---
description: クローズドキャプショントラックのスタイル設定情報を指定するには、 TextFormat クラスを使用します。このクラスは、プレーヤーが表示するクローズドキャプションのスタイルを設定します。
title: クローズドキャプションのスタイル設定を制御する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# クローズドキャプションのスタイル設定を制御する {#control-closed-caption-styling}

クローズドキャプショントラックのスタイル設定情報を指定するには、 TextFormat クラスを使用します。このクラスは、プレーヤーが表示するクローズドキャプションのスタイルを設定します。

このクラスは、フォントタイプ、サイズ、色、背景の不透明度など、クローズドキャプションのスタイル設定情報をカプセル化します。

## クローズドキャプションのスタイルの設定 {#section_C9B5E75C70DD42E59DC4DD0F308C8216}

TVSDK メソッドを使用して、クローズドキャプションのテキストのスタイルを設定できます。

1. メディアプレーヤーが少なくとも `PREPARED` ステータス。
1. の作成 `TextFormatBuilder` インスタンス。

   すべてのクローズドキャプションスタイル設定パラメーターを今すぐ指定することも、後で設定することもできます。

   TVSDK は、クローズドキャプションのスタイル設定情報を `TextFormat` インターフェイス。 The `TextFormatBuilder` クラスは、このインターフェイスを実装するオブジェクトを作成します。

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

1. を実装するオブジェクトへの参照を取得するには `TextFormat` インターフェイスで、 `TextFormatBuilder.toTextFormat` パブリックメソッド。

   これにより、 `TextFormat` オブジェクトを再生する必要があります。

   `public TextFormat toTextFormat()`


1. オプションで、次のいずれかの操作を行って、現在のクローズドキャプションスタイル設定を取得します。

   * ですべてのスタイル設定を取得する `MediaPlayer.getCCStyle` 戻り値は、 `TextFormat` インターフェイス。

     ```java
     /** 
     * @return the current closed captioning style.  
     * If no style was previously set, it returns a TextFormat object 
     * with default values for each attribute. 
     * @throws MediaPlayerException if media player was already released. 
     */ 
     public TextFormat getCCStyle() throws MediaPlayerException;
     ```

   * 以下の手順で、一度に 1 つずつ設定を取得します。 `TextFormat` インターフェイスの getter メソッド。

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

   * setter メソッドの使用 `MediaPlayer.setCCStyle`を渡す場合、 `TextFormat` インターフェイス：

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

   * 以下を使用します。 `TextFormatBuilder` 個々の setter メソッドを定義するクラス。

     The `TextFormat` インターフェイスは不変オブジェクトを定義するので、getter メソッドのみが存在し、setter メソッドは存在しません。 クローズドキャプションのスタイル設定パラメーターは、 `TextFormatBuilder` クラス：

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
     >**カラー設定：** Android TVSDK 2.X では、クローズドキャプションのカラースタイル設定が強化されました。 この機能強化により、クローズドキャプションの色を、RGBの色の値を表す 16 進文字列を使用して設定できます。 RGBの 16 進数カラー表現は、Photoshopなどのアプリケーションで使用する一般的な 6 バイト文字列です。
     >
     >* FFFFFF =黒
     >* 000000 =白
     >* FF0000 =赤
     >* 00FF00 =緑
     >* 0000FF =青
     >など。
     >
     >アプリケーションで、カラースタイル情報をに渡す際に使用する `TextFormatBuilder`を使用している場合、 `Color` 以前と同様に列挙しますが、次にを追加する必要があります。 `getValue()` 値を文字列として取得する色に設定します。 例：
     >
     >`tfb = tfb.setBackgroundColor(TextFormat.Color.RED      <b>.getValue()</b>);`

クローズドキャプションスタイルの設定は非同期的な操作なので、変更が画面に表示されるまでに数秒かかる場合があります。

## クローズドキャプションのスタイル設定オプション {#section_6D685EC2D58C42A2BDDD574EDFCCC2A0}

複数のキャプションのスタイル設定オプションを指定できます。これらのオプションは、元のキャプションのスタイルオプションよりも優先されます。

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
>デフォルト値を定義するオプション ( 例： `DEFAULT`) の値は、キャプションが最初に指定されたときの設定を示します。

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
   <td colname="1"> フォントエッジ </td> 
   <td colname="2"> <p>フォントの端に使用する効果（浮き出し、なしなど）。 </p> <p>は、 <span class="codeph"> TextFormat.FontEdge </span> 列挙。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> フォントカラー </td> 
   <td colname="2"> <p>フォントの色。 </p> <p>は、 <span class="codeph"> TextFormat.Color </span> 列挙。 </p> </td> 
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
   <td colname="2"> <p>テキストが配置されているウィンドウの背景の色。 </p> <p>には、フォントカラーに使用できる任意の値を設定できます。 </p> </td> 
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
  <tr rowsep="1"> 
   <td colname="1"> 下のインセット </td> 
   <td colname="2"> <p>キャプションウィンドウの下端からの、避ける垂直方向の距離。 </p> <p>キャプションウィンドウの高さに対する割合（「20%」など）またはピクセル数（「20」など）で表します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> 安全な領域 </td> 
   <td colname="2"> <p>画面の端の周りの 0%～25%（キャプションは表示されない）の領域。 </p> <p>デフォルトでは、WebVTT の安全な領域は 0%です。 この設定を使用すると、アプリケーションがそのデフォルトを上書きできます。 2 つの値（例えば、文字列「10%,20%」）を指定した場合、最初の値は水平方向のセーフエリア、2 番目の値は垂直方向のセーフエリアになります。 1 つの値（文字列「15%」など）を指定した場合、垂直軸と水平軸の両方で、指定した安全な領域が使用されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## キャプションの書式設定の例 {#section_58E8E82494EC4683B010FFDE67485CF9}

クローズドキャプションの書式設定の指定方法を示す例を以下に示します。

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
