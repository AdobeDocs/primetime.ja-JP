---
description: MediaPlayerView オブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
title: ビデオビューの位置とサイズの制御
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# ビデオビューの位置とサイズの制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerView オブジェクトを使用して、ビデオビューの位置とサイズを制御できます。

ブラウザー TVSDK は、アプリケーション、プロファイルスイッチ、コンテンツスイッチなどによって行われた変更によってビデオのサイズや位置が変わるたびに、ビデオビューの縦横比をデフォルトで維持しようとします。

異なる *スケールポリシー*. を使用してスケールポリシーを指定します。 `MediaPlayerView` オブジェクトの `scalePolicy` プロパティ。 のデフォルトのスケールポリシー `MediaPlayerView` が `MaintainAspectRatioScalePolicy` クラス。 スケールポリシーをリセットするには、 `MaintainAspectRatioScalePolicy` オン `MediaPlayerView.scalePolicy` 自分の政策で

>[!IMPORTANT]
>
>次の項目は設定できません： `scalePolicy` プロパティを null 値に設定します。

## 非Flashフォールバックシナリオ {#non-flash-fallback-scenarios}

非Flashフォールバックシナリオでは、スケールポリシーが正しく機能するために、 `View` コンストラクタは、 `offsetWidth` および `offsetHeight`. 誤った関数の例を示すために、ビデオの div 要素の幅と高さが css で明示的に設定されていない場合は、 `View` コンストラクタは 0 を返します。 `offsetWidth` または `offsetHeight`.

>[!NOTE]
>
>CustomScalePolicy は、IE、Edge、Safari 9 をはじめとするいくつかのブラウザーに対するサポートが制限されています。 これらのブラウザーでは、ビデオのネイティブの縦横比は変更できません。 ただし、ビデオの位置とサイズは、スケールポリシーに従って適用されます。

1. の実装 `MediaPlayerViewScalePolicy` 独自のスケールポリシーを作成するためのインターフェイス。

   The `MediaPlayerViewScalePolicy` には 1 つのメソッドがあります。

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

1. 実装を `MediaPlayerView` プロパティ。

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. メディアプレーヤーにビューを追加する `view` プロパティ。

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**例：縦横比を維持せずに、ビデオ全体が表示されるようにビデオを拡大・縮小します。**

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
