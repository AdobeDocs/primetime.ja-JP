---
description: MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。
seo-description: MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。
seo-title: ビデオ表示の位置とサイズの制御
title: ビデオ表示の位置とサイズの制御
uuid: 2231c574-03cd-45a8-ab00-4a42f8e044f0
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# ビデオ表示の位置とサイズの制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。

TVSDKは、ビデオのサイズや位置が変更されると(アプリケーション、プロファイルスイッチ、コンテンツの切り替えによる変更などが原因で)、デフォルトでビデオ表示の縦横比を維持しようとします。

別のス *ケールポリシーを指定すると、デフォルトの縦横比の動作を上書きできます*。 オブジェクトのプロパティを使用して、スケ `MediaPlayerView` ールポリシーを指定し `scalePolicy` ます。 デフォルト `MediaPlayerView`のスケールポリシーは、クラスのインスタンスを使用して設定され `MaintainAspectRatioScalePolicy` ます。 スケールポリシーをリセットするには、onのデフォルトインスタンス `MaintainAspectRatioScalePolicy` を独自のポリシー `MediaPlayerView.scalePolicy` に置き換えます。 (この `scalePolicy` プロパティをnull値に設定することはできません)。

1. 独自のスケールポリシーを作成するには、 `MediaPlayerViewScalePolicy` インターフェイスを実装します。

   に `MediaPlayerViewScalePolicy` は次の方法があります。

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDKは、ビデオの表示に `StageVideo` オブジェクトを使用します。 `StageVideo` オブジェクトは表示リスト上にないので、この `viewPort` パラメーターにはビデオの絶対座標が含まれます。
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

1. 実装をプ `MediaPlayerView` ロパティに割り当てます。

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. Media Player追加のプロパティへの表示。 `view`

   ```
   addChild(view); 
   
   mediaPlayer.view = view;
   ```

<!--<a id="example_7B08ECCDA17B4DD191FC672BD1F4C850"></a>-->

**次に例を示します。縦横比を維持せずに、ビデオ表示全体に合わせてビデオを拡大・縮小します。**

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

