---
description: TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。
title: 再生イベントの順序
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# 再生イベントの順序{#order-of-playback-events}

TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* `MediaPlayer.replaceCurrentResource`を介してメディアリソースを正常に読み込むと、次の順序でイベントされます。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.INITIALIZED`

* `MediaPlayer.prepareToPlay`を介して再生を準備する場合、イベントの順序は次のとおりです。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` 広告が挿入された場合
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.PREPARED`

* ライブ/リニアストリームの場合、再生中、再生時間が進み、追加のオポチュニティが解決されると、次の順序でイベントが発生します。

   * `MediaPlayerItemEvent.ITEM_UPDATED`
   * `TimelineEvent.TIMELINE_UPDATED` 広告が挿入された場合

<!--<a id="section_76C13548AF934868B70757CA5489E516"></a>-->

次の例に、イベントの一般的な流れを示します。

```
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_CREATED, onItemCreated); 
public function onItemCreated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerItemEvent.ITEM_UPDATED, onItemUpdated); 
public function onItemUpdated(event:MediaPlayerItemEvent):void { 
    var item:MediaPlayerItem = event.item; 
    ... 
} 
mediaPlayer.addEventListener(MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
                             onStatusChanged); 
public function onStatusChanged(event:MediaPlayerStatusChangeEvent):void { 
    switch(event.status){ 
        case MediaPlayerStatus.INITIALIZING: 
        case MediaPlayerStatus.INITIALIZED: 
        ... 
    } 
    ... 
} 
mediaPlayer.addEventListener(TimeChangeEvent.TIME_CHANGED, onTimeChanged); 
public function onTimeChanged(event:TimeChangeEvent):void { 
    var timeInMilliseconds:Number = event.time; 
    ... 
}
```

