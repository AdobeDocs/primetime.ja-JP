---
description: TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-description: TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。
seo-title: 再生イベントの順序
title: 再生イベントの順序
uuid: 4a9ea66b-a383-46ff-9ab8-983b1dd7f935
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 再生イベントの順序{#order-of-playback-events}

TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* メディアリソースを通じて正常に読み込む `MediaPlayer.replaceCurrentResource`と、イベントの順序は次のとおりです。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.INITIALIZED`

* 通じて再生を準備する場合、 `MediaPlayer.prepareToPlay`イベントの順序は次のとおりです。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` 広告が挿入された場合
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.PREPARED`

* ライブ/リニアストリームの場合、再生時間が進み、追加のオポチュニティが解決されるに従って、再生中に、イベントの順序は次のとおりです。

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

