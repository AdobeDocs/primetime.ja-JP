---
description: MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。
title: ビデオ表示の位置とサイズの制御
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---


# ビデオ表示の位置とサイズを制御{#control-the-position-and-size-of-the-video-view}

MediaPlayerViewオブジェクトを使用して、ビデオ表示の位置とサイズを制御できます。

TVSDKは、ビデオのサイズや位置が変更されると(アプリケーション、プロファイルスイッチ、コンテンツの切り替えによる変更などが原因で)、デフォルトでビデオ表示の縦横比を維持しようとします。

異なる&#x200B;*スケールポリシー*&#x200B;を指定すると、デフォルトの縦横比の動作を上書きできます。 `MediaPlayerView`オブジェクトの`scalePolicy`プロパティを使用して、スケールポリシーを指定します。 `MediaPlayerView`のデフォルトのスケールポリシーは、`MaintainAspectRatioScalePolicy`クラスのインスタンスを使用して設定されます。 スケールポリシーをリセットするには、`MediaPlayerView.scalePolicy`の`MaintainAspectRatioScalePolicy`のデフォルトインスタンスを独自のポリシーに置き換えます。 （`scalePolicy`プロパティをnull値に設定することはできません）。

1. `MediaPlayerViewScalePolicy`インターフェイスを実装して、独自のスケールポリシーを作成します。

   `MediaPlayerViewScalePolicy`には次のメソッドが1つあります。

   ```
   public function adjust(viewPort:Rectangle, 
     videoWidth:Number, videoHeight:Number):Rectangle;
   ```

   >[!NOTE]
   >
   >TVSDKは、ビデオの表示に`StageVideo`オブジェクトを使用します。`StageVideo`オブジェクトは表示リスト上にないので、`viewPort`パラメーターにはビデオの絶対座標が含まれます。
   >
   >
   >例：
   >
   >
   ```
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

1. 実装を`MediaPlayerView`プロパティに割り当てます。

   ```
   var view:MediaPlayerView = MediaPlayerView.create(stage.stageVideos[0]); 
   view.scalePolicy = new CustomScalePolicy();
   ```

1. メディアプレ追加イヤーの`view`プロパティへの表示。

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

