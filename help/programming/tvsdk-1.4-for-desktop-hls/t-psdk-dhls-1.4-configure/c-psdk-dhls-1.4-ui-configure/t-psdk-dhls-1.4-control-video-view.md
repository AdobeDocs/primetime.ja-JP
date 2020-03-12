---
description: MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
seo-description: MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
seo-title: ビデオビューの位置とサイズの制御
title: ビデオビューの位置とサイズの制御
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ビデオビューの位置とサイズの制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerViewオブジェクトを使用して、ビデオビューの位置とサイズを制御できます。

TVSDKは、ビデオのサイズや位置が変わるたびに（アプリケーション、プロファイルの切り替え、コンテンツの切り替えなどによって）、ビデオビューの縦横比を維持しようとします。

別のスケールポリシーを指定することで、デフォルトの縦横比の動作を上書きする *ことができま*&#x200B;す。 オブジェクトのプロパティを使用して、ス `MediaPlayerView` ケールポリシーを指 `scalePolicy` 定します。 のデフォ `MediaPlayerView`ルトのスケールポリシーは、クラスのインスタンスを使用して設定さ `MaintainAspectRatioScalePolicy` れます。 スケールポリシーをリセットするには、のデフォルトのインスタンスを `MaintainAspectRatioScalePolicy` 独自のポ `MediaPlayerView.scalePolicy` リシーで置き換えます。 (プロパティをnull値 `scalePolicy` に設定することはできません)。

1. 独自のスケール `MediaPlayerViewScalePolicy` ポリシーを作成するには、インターフェイスを実装します。

   には次の1 `MediaPlayerViewScalePolicy` つの方法があります。

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDKは、ビデオの表 `StageVideo` 示にオブジェクトを使用します。オブジェクトは表 `StageVideo` 示リストにないので、パラメーターにはビデ `viewPort` オの絶対座標が含まれています。
   >
   >
   >例：   >
   >
   >
   ```>
   >public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
   >       /** 
   >         * Default constructor. 
   >         */ 
   >       public function CustomScalePolicy() { 
   >       } 
   > 
   >    
      public function adjust(viewPort:Rectangle,  
   >                                                     videoWidth:Number,  
   >                                                     videoHeight:Number):Rectangle { 
   >               return customAdjustment(); 
   >       } 
   > 
   >    
      public function customAdjustment():Rectangle { 
   >               /* Your custom adjustment here */ 
   >               [...] 
   >       } 
   >}
   >```   >
   >



1. 実装をプロパティに割り当 `MediaPlayerView` てます。

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. ビューをMedia Playerのプロパティに追加し `view` ます。

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**例：縦横比を維持せずに、ビデオビュー全体に表示されるようにビデオを拡大・縮小します。**

```
package com.adobe.mediacore.samples.utils { 
    import com.adobe.mediacore.view.MediaPlayerViewScalePolicy; 
    import flash.geom.Rectangle; 
 
    /** 
    * A very simple custom scale policy - the video will fill the entire 
    * allocated space. The aspect ratio will not be kept. 
    */ 
    public class CustomScalePolicy implements MediaPlayerViewScalePolicy { 
 
        /** 
        * Default constructor. 
        */ 
        public function CustomScalePolicy() { 
        } 
 
        public function adjust(viewPort:Rectangle, 
                               videoWidth:Number,  
                               videoHeight:Number):Rectangle { 
            return viewPort; 
        } 
    } 
} 
 
var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
view.scalePolicy = new CustomScalePolicy(); 
addChild(view); 
mediaPlayer.view = view;
```

