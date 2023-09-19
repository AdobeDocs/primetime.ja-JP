---
description: TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。
title: 再生イベントの順序
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# 再生イベントの順序{#order-of-playback-events}

TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

<!--<a id="section_6E34A6C7936245D88DEB3315DA64598B"></a>-->

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* を介してメディアリソースを正常に読み込んだ場合 `MediaPlayer.replaceCurrentResource`の場合、イベントの順序は次のとおりです。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.INITIALIZING`

   * `MediaPlayerItemEvent.ITEM_CREATED`
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.INITIALIZED`

* を使用して再生を準備する場合 `MediaPlayer.prepareToPlay`の場合、イベントの順序は次のとおりです。

   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.PREPARING`

   * `TimelineEvent.TIMELINE_UPDATED` 広告が挿入された場合
   * `MediaPlayerStatusChangeEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.PREPARED`

* ライブ/リニアストリームの場合、再生中に、再生ウィンドウが進み、追加のオポチュニティが解決されると、イベントの順序は次のようになります。

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
