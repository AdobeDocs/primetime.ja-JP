---
description: イベントハンドラーを使用すると、TVSDK イベントに応答できます。
title: イベントリスナーとコールバックの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# イベントリスナーとコールバックの実装  {#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、TVSDK イベントに応答できます。

イベントが発生すると、 TVSDK のイベントメカニズムは登録されたイベントハンドラーを呼び出し、そのハンドラーにイベント情報を渡します。

TVSDK は、リスナーを、 `MediaPlayer` インターフェイス。

アプリケーションは、アプリケーションに影響を与える TVSDK イベントに対してイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要があるイベントを決定します。

   * 必須イベント：すべての再生イベントをリッスンします。

     >[!IMPORTANT]
     >
     >ステータス変更イベントをリッスンします。このイベントは、プレーヤーのステータスが知る必要のある方法で変更されたときに発生します。 提供される情報には、プレーヤーが次に実行できる操作に影響を与える可能性のあるエラーが含まれます。

   * アプリケーションに応じたその他のイベントについては、  [Primetime プレーヤーイベントの概要](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

1. 各イベントのイベントリスナーを実装し、追加します。

   ほとんどのイベントに対して、 TVSDK はイベントリスナーに引数を渡します。 このような値は、イベントに関する情報を提供し、次に何をおこなうかを決定するのに役立ちます。 The `MediaPlayerEvent` 列挙では、 `MediaPlayer` が発行されました。 詳しくは、  [Primetime プレーヤーイベントの概要](../../android-3x-events-notifications/events-summary/android-3x-events-summary.md).

   例えば、 `mPlayer` は、 `MediaPlayer`イベントリスナーの追加方法と構造を次に示します。

   ```java
   mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() { 
       @Override 
       public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
           event.getMetadata(); 
           if (event.getMetadata() != null) {/* Do something */} 
           if (event.getStatus() == MediaPlayerStatus.IDLE) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.INITIALIZED) {/* Do something */} 
           else if (event.getStatus() == MediaPlayerStatus.PREPARED) {/* Do something */} 
       } 
   }); 
   ```

## 再生イベントの順序 {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

次の例は、再生中に発生する一部のイベントの順序を示しています。

を介してメディアリソースを正常に読み込んだ場合 `MediaPlayer.replaceCurrentResource`の場合、イベントの順序は次のとおりです。

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>メディアリソースをメインスレッドに読み込みます。 メディアリソースをバックグラウンドスレッドに読み込むと、この操作または後続の操作で次のようなエラーが発生する場合があります。 `MediaPlayerException`、および終了します。

を使用して再生を準備する場合 `MediaPlayer.prepareToPlay`の場合、イベントの順序は次のとおりです。

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合。
1. `MediaPlayerEvent.STATUS_CHANGED` ステータス別 `MediaPlayerStatus.PREPARED`

ライブ/リニアストリームの場合、再生中に、再生ウィンドウが進み、追加のオポチュニティが解決されると、イベントの順序は次のようになります。

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合

## 広告イベントの順序 {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

再生に広告が含まれている場合、 TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

広告を再生する際のイベントの順序は次のとおりです。

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

広告ブレーク内の各広告に対して、次のイベントがディスパッチされます。

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

次の例に、広告再生イベントの一般的な進行を示します。

```
mediaPlayer.addEventListener(MediaPlayerEvent.AD_RESOLUTION_COMPLETE, new AdResolutionCompleteEventListener() { 
        @Override 
        public void onAdResolutionComplete() { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_START, new AdBreakStartedEventListener() { 
         @Override 
        public void onAdBreakStarted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_START, new AdStartedEventListener() { 
         @Override 
        public void onAdStarted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_PROGRESS, new AdProgressEventListener() { 
         @Override 
         public void onAdProgress(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_COMPLETE, new AdCompletedEventListener() { 
         @Override 
         public void onAdCompleted(AdPlaybackEvent adPlaybackEvent) { ... } 
    }); 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_BREAK_COMPLETE, new AdBreakCompletedEventListener() { 
         @Override 
         public void onAdBreakCompleted(AdBreakPlaybackEvent adBreakPlaybackEvent) { ... } 
    }); 
 
Below event is for tracking ad clicks. 
 
mediaPlayer.addEventListener(MediaPlayerEvent.AD_CLICK, new AdClickedEventListener() { 
         @Override 
         public void onAdClicked(AdClickEvent adClickEvent) { ... } 
    });
```

## DRM イベントの順序 {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。 プレーヤーは、これらのイベントに応じてアクションを実装できます。

DRM 関連のすべてのイベントに関する通知を受け取るには、 `MediaPlayerEvent.DRM_METADATA`. TVSDK は、 `DRMManager` クラス。

## ローダーイベントの順序 {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDK がディスパッチする `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` ローダイベントが発生した場合。
