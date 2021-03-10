---
description: MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。
title: ビデオ表示の位置とサイズの制御
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# ビデオ表示の位置とサイズを制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。

アプリケーション、プロファイルスイッチ、コンテンツスイッチなどによって行われた変更によってビデオのサイズや位置が変わった場合は、ブラウザーTVSDKは、デフォルトでビデオ表示の縦横比を維持しようとします。

異なる&#x200B;*スケールポリシー*&#x200B;を指定すると、デフォルトの縦横比の動作を上書きできます。 `MediaPlayerView`オブジェクトの`scalePolicy`プロパティを使用して、スケールポリシーを指定します。 `MediaPlayerView`のデフォルトのスケールポリシーは、`MaintainAspectRatioScalePolicy`クラスのインスタンスを使用して設定されます。 スケールポリシーをリセットするには、`MediaPlayerView.scalePolicy`の`MaintainAspectRatioScalePolicy`のデフォルトインスタンスを独自のポリシーに置き換えます。

>[!IMPORTANT]
>
>`scalePolicy`プロパティをnull値に設定することはできません。

## Flash以外のフォールバックシナリオ{#non-flash-fallback-scenarios}

Flash以外のフォールバックシナリオでは、スケールポリシーが正しく機能するために、`View`コンストラクターで指定されたビデオdiv要素は、`offsetWidth`と`offsetHeight`に対してゼロ以外の値を返す必要があります。 誤った関数の例を示すために、ビデオdiv要素の幅と高さがcssで明示的に設定されていない場合、`View`コンストラクタは、`offsetWidth`または`offsetHeight`に対して0を返します。

>[!NOTE]
>
>CustomScalePolicyでは、IE、Edge、Safari 9など、一部のブラウザーのサポートが制限されています。 これらのブラウザーでは、ビデオのネイティブの縦横比は変更できません。 ただし、ビデオの位置とサイズは、スケールポリシーに従って適用されます。

1. `MediaPlayerViewScalePolicy`インターフェイスを実装して、独自のスケールポリシーを作成します。

   `MediaPlayerViewScalePolicy`には次のメソッドが1つあります。

   ```js
   /** 
   * Adjust the specified rectangle to match the new video dimensions. 
   * @param viewPort {AdobePSDK.Rectangle}The video rectangle as absolute position. 
   * @param videoWidth {Number}The video width. 
   * @param videoHeight {Number} The video height. 
   * @return {AdobePSDK.Rectangle} an adjusted rectangle. 
   */ 
   function adjustCallbackFunc(viewPort, videoWidth, videoHeight);
   ```

   例：

   ```js
   /** 
   Default Constructor 
   */ 
   MediaPlayerViewCustomScalePolicy = function() { 
       return this; 
   }; 
   MediaPlayerViewCustomScalePolicy.prototype = { 
       constructor: MediaPlayerViewScalePolicy, 
       adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
           /* Your Custom Adjustment here. */ 
           [...] 
           return adjustedRectangle; 
       } 
   };
   ```

1. 実装を`MediaPlayerView`プロパティに割り当てます。

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. メディアプレ追加イヤーの`view`プロパティへの表示。

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**次に例を示します。縦横比を維持せずに、ビデオ表示全体に合わせてビデオを拡大・縮小します。**

```
/** 
 * Default constructor. 
 */ 
MediaPlayerViewCustomScalePolicy = function() { 
    return this; 
}; 
MediaPlayerViewCustomScalePolicy.prototype = { 
    constructor: MediaPlayerViewScalePolicy, 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    adjustCallbackFunc: function(viewPort, videoWidth, videoHeight) { 
        return viewPort; 
    } 
}; 
var view = new AdobePSDK.MediaPlayerView(videoDiv); 
view.scalePolicy = new MediaPlayerViewCustomScalePolicy (); 
mediaPlayer.view = view;
```

