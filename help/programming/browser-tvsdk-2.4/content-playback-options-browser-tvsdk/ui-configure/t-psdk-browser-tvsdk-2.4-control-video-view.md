---
description: MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
seo-description: MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
seo-title: ビデオビューの位置とサイズの制御
title: ビデオビューの位置とサイズの制御
uuid: d09dbc18-1ec0-4336-bf3f-7ff6c265c443
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# ビデオビューの位置とサイズの制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。

ブラウザーTVSDKは、アプリケーション、プロファイルスイッチ、コンテンツスイッチなどによって行われた変更によってビデオのサイズや位置が変更された場合、デフォルトでビデオビューの縦横比を維持しようとします。

別のスケールポリシーを指定することで、デフォルトの縦横比の動作を上書きする *ことができま*&#x200B;す。 オブジェクトのプロパティを使用して、ス `MediaPlayerView` ケールポリシーを指 `scalePolicy` 定します。 のデフォルトのスケールポリシ `MediaPlayerView` ーは、クラスのインスタンスで設定さ `MaintainAspectRatioScalePolicy` れます。 スケールポリシーをリセットするには、のデフォルトのインスタンスを `MaintainAspectRatioScalePolicy` 独自のポ `MediaPlayerView.scalePolicy` リシーで置き換えます。

>[!IMPORTANT]
>
>プロパティをnull値に設 `scalePolicy` 定することはできません。

## Flash以外のフォールバックシナリオ {#non-flash-fallback-scenarios}

Flash以外のフォールバックシナリオでは、スケールポリシーが正しく機能するために、コンストラクターで指定されたビデオdiv要素は、 `View` およびのゼロ以外の値を返す必要が `offsetWidth` ありま `offsetHeight`す。 誤った関数の例を示すため、ビデオdiv要素の幅と高さがCSSで明示的に設定されていない場合、コンストラクタはまたはに対して0 `View` を返すことが `offsetWidth` ありま `offsetHeight`す。

>[!NOTE]
>
>CustomScalePolicyは、IE、Edge、Safari 9など、一部のブラウザーでのサポートに制限があります。 これらのブラウザーでは、ビデオのネイティブの縦横比は変更できません。 ただし、ビデオの位置とサイズは、スケールポリシーに従って適用されます。

1. 独自のスケール `MediaPlayerViewScalePolicy` ポリシーを作成するには、インターフェイスを実装します。

   には次の1 `MediaPlayerViewScalePolicy` つの方法があります。

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

1. 実装をプロパティに割り当 `MediaPlayerView` てます。

   ```js
   var view = new AdobePSDK.MediaPlayerView(videoDiv); 
   view.scalePolicy= new MediaPlayerViewCustomScalePolicy();
   ```

1. ビューをMedia Playerのプロパティに追加し `view` ます。

   ```
   mediaplayer.view = view;
   ```

<!--<a id="example_ABCD79AE29DB4A668F9A8B729FE44AF9"></a>-->

**例：縦横比を維持せずに、ビデオビュー全体に表示されるようにビデオを拡大・縮小します。**

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

