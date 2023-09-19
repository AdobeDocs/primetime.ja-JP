---
title: UI フレームワークを使用した基本的なプレーヤーの作成
description: UI フレームワークを使用した基本的なプレーヤーの作成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# UI フレームワークを使用した基本的なプレーヤーの作成{#create-a-basic-player-using-the-ui-framework}

UI フレームワークを使用して基本的なプレーヤーを作成するには、次の手順を実行します。

1. の作成 `<div>` （プレーヤーインスタンス用）。

   例：

   ```
   <div id="video1" > 
    </div>
   ```

1. プレーヤーを読み込みます。

   ```js
   <script> 
       (function(){ 
           var player = ptp.videoPlayer('#video1'); 
       })(); 
   </script>
   ```

   プレーヤーを作成する際に、指定した `<div>` 要素に次の CSS クラスが与えられる： `ptp-main-video-div-style`. 結果の DOM は次のようになります。

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <video class="vp-video-element"></video> 
   </div>
   ```

1. UI コントロールを追加します。

   例えば、マウスをプレーヤーに合わせたときに表示されるコントロールバーを追加します。

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

   結果の DOM は次のように表示されます。

   ```
   <div id="video1" class="ptp-main-video-div-style"> 
       <div class="ptp-control-bar my_control_bar"></div> 
       <video class="vp-video-element"></video> 
   </div>
   ```

の呼び出しから返されたオブジェクト `ptp.videoPlayer()` は、 TVSDK メディアプレイヤー API をラップする動作を提供し、再生をプログラムで制御できます。 メディアプレーヤーインスタンスを呼び出すと、ユーザーインターフェイスは、メディアプレーヤーで発生したイベントに基づいて更新されます。

```js
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
        player.loadResource( 'sample.mp4' ); 
    })(); 
</script>
```
