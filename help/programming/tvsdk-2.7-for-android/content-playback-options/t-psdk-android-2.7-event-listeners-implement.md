---
description: イベントハンドラーを使用すると、TVSDKイベントに応答できます。
seo-description: イベントハンドラーを使用すると、TVSDKイベントに応答できます。
seo-title: イベントリスナーとコールバックの実装
title: イベントリスナーとコールバックの実装
uuid: bb1980f3-340b-4d36-ae7e-c9fc1d145233
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# イベントリスナーとコールバックの実装 {#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、TVSDKイベントに応答できます。

イベントが発生すると、TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報を渡します。

TVSDKは、リスナーをインターフェイス内のパブリック内部インターフェイスとして定 `MediaPlayer` 義します。

アプリケーションに影響を与えるTVSDKイベントのイベントリスナーを、アプリケーションで実装する必要があります。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * 必要なイベント：すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >プレイヤーのステータスが必要な方法で変化した場合に発生するステータス変更イベントをリッスンします。 提供される情報には、プレイヤーが次に実行できる操作に影響を与える可能性のあるエラーが含まれます。

   * その他のイベントについては、使用しているアプリケーションに応じて、events-summaryを参照してください。

1. 各イベントのイベントリスナーを実装し、追加します。

   >[!NOTE]
   >
   >ほとんどのイベントで、TVSDKはイベントリスナーに引数を渡します。 この値は、イベントに関する情報を提供し、次に何を行うかを決定するのに役立ちます。 列挙は、 `MediaPlayerEvent` ディスパッチするすべてのイベントを一覧 `MediaPlayer` 表示します。 詳しくは、events-summaryを参照してください。

   例えば、がのイン `mPlayer` スタンスの場合、 `MediaPlayer`次の方法でイベントリスナーを追加し、構成します。

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

TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

次の例は、再生中に発生する一部のイベントの順序を示しています。

メディアリソースを通じて正常に読み込む `MediaPlayer.replaceCurrentResource`と、イベントの順序は次のとおりです。

1. `MediaPlayerEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>メインスレッドにメディアリソースを読み込みます。 バックグラウンドスレッドにメディアリソースを読み込むと、この操作またはその後の操作で、やなどのエラーが発生する `MediaPlayerException`場合があります。

通じて再生を準備する場合、 `MediaPlayer.prepareToPlay`イベントの順序は次のとおりです。

1. `MediaPlayerEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合。
1. `MediaPlayerEvent.STATUS_CHANGED` 身分が `MediaPlayerStatus.PREPARED`

ライブ/リニアストリームの場合、再生時間が進み、追加のオポチュニティが解決されるに従って、再生中に、イベントの順序は次のとおりです。

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合

## 広告イベントの順序 {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

再生に広告が含まれる場合、TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、期待されたシーケンス内のイベントに基づいてアクションを実装できます。

広告を再生する場合、イベントの順序は次のとおりです。

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

次のイベントが、広告の時間内のすべての広告に対してディスパッチされます。

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

次の例は、広告再生イベントの一般的な流れを示しています。

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

## DRMイベントの順序 {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。

すべてのDRM関連イベントに関する通知を受け取るには、をリッスンしま `MediaPlayerEvent.DRM_METADATA`す。 TVSDKは、クラスを通じて追加のDRMイベントをディスパッ `DRMManager` チします。

## ローダイベントの順序 {#section_5638F8EDACCE422A9425187484D39DCC}

TVSDKは、ローダイベ `MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE` ントが発生するとディスパッチします。