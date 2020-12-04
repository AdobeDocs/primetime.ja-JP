---
description: 'null'
seo-description: 'null'
seo-title: UIフレームワークを使用した基本プレーヤーの作成
title: UIフレームワークを使用した基本プレーヤーの作成
uuid: d1a82dbb-1c05-4d0c-b6bc-e07cbede93cb
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 1%

---


# UIフレームワーク{#create-a-basic-player-using-the-ui-framework}を使用した基本プレーヤーの作成

UIフレームワークを使用して基本プレーヤーを作成するには：

1. 使用するプレーヤーインスタンスの`<div>`を作成します。

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

   プレイヤーが作成されると、指定した`<div>`要素に`ptp-main-video-div-style`のCSSクラスが与えられます。 結果のDOMは次のように表示されます。

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. UIコントロ追加ール。

   例えば、プレーヤーにマウスを合わせたときに表示されるコントロールバーを追加します。

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

`ptp.videoPlayer()`の呼び出しから返されるオブジェクトは、TVSDKメディアプレイヤーAPIをラップする動作を提供し、プログラムによる再生の制御を可能にします。 メディアプレイヤーインスタンスを呼び出すと、メディアプレイヤーが呼び出したイベントに基づいて、ユーザーインターフェイスが更新されます。

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
