---
description: MediaPlayerView オブジェクトを使用して、ビデオビューの位置とサイズを制御できます。
title: ビデオビューの位置とサイズの制御
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# ビデオビューの位置とサイズの制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerView オブジェクトを使用して、ビデオビューの位置とサイズを制御できます。

TVSDK は、（アプリケーションやプロファイルの切り替え、コンテンツの切り替えなどによって）ビデオのサイズや位置が変わるたびに、デフォルトでビデオビューの縦横比を維持しようとします。

異なる *スケールポリシー*. を使用してスケールポリシーを指定します。 `MediaPlayerView` オブジェクトの `scalePolicy` プロパティ。 The `MediaPlayerView`のデフォルトのスケールポリシーは、 `MaintainAspectRatioScalePolicy` クラス。 スケールポリシーをリセットするには、 `MaintainAspectRatioScalePolicy` オン `MediaPlayerView.scalePolicy` 自分の政策で ( `scalePolicy` プロパティを null 値に設定します。)

1. の実装 `MediaPlayerViewScalePolicy` 独自のスケールポリシーを作成するためのインターフェイス。

   The `MediaPlayerViewScalePolicy` には 1 つのメソッドがあります。

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDK は、 `StageVideo` ビデオを表示するオブジェクト、および `StageVideo` オブジェクトが表示リストにない場合、 `viewPort` パラメーターには、ビデオの絶対座標が含まれます。
   >
   >
   >例：
   >
   >```
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
   >```
   >

1. 実装を `MediaPlayerView` プロパティ。

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. メディアプレーヤーにビューを追加する `view` プロパティ。

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**例：縦横比を維持せずに、ビデオ全体が表示されるようにビデオを拡大・縮小します。**

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
