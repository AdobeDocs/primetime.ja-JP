---
description: 'null'
seo-description: 'null'
seo-title: UIフレームワークを使用した基本プレーヤーの作成
title: UIフレームワークを使用した基本プレーヤーの作成
uuid: d1a82dbb-1c05-4d0c-b6bc-e07cbede93cb
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# UIフレームワークを使用した基本プレーヤーの作成{#create-a-basic-player-using-the-ui-framework}

UIフレームワークを使用して基本プレーヤーを作成するには：

1. プレーヤーイン `<div>` スタンスのを作成します。

   例：

   ```
   <div id="video1" > 
    </div>
   ```

1. プレイヤーを読み込みます。

   ```js
   <script> 
       (function(){ 
           var player = ptp.videoPlayer('#video1'); 
       })(); 
   </script>
   ```

   プレイヤーが作成されると、指定した `<div>` 要素にのCSSクラスが与えられま `ptp-main-video-div-style`す。 結果のDOMは次のように表示されます。

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. UIコントロールを追加します。

   例えば、マウスをプレーヤーの上に置くと表示されるコントロールバーを追加します。

   ```js
   <script> 
       (function(){ 
           function myControlBarBehavior(element, configuration, player) { 
               return ptp.controlBarBehavior(element, configuration, player); 
           } 
           var player = ptp.videoPlayer('#video1', { 
               controlBar: { 
                   behavior: myControlBarBehavior, 
                   classNames: 'ptp-control-bar my_control_bar' 
               } 
           }); 
       })(); 
   </script>
   ```

   結果のDOMは次のように表示されます。

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <div class="ptp-control-bar my_control_bar"></div> 
       <video class="vp-video-element"></video> 
   </div>
   ```

呼び出しから返されるオブジェクト `ptp.videoPlayer()` は、TVSDKメディアプレイヤーAPIをラップする動作を提供し、プログラム的に再生を制御できます。 メディアプレイヤーインスタンスを呼び出すと、ユーザーインターフェイスは、メディアプレイヤーが発生したイベントに基づいて更新されます。

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
