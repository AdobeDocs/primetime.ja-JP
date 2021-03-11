---
description: イベントハンドラーを使用すると、TVSDKイベントに応答できます。
title: イベントリスナーとコールバックの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# イベントリスナーとコールバックを実装する{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、TVSDKイベントに応答できます。

イベントが発生すると、TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報を渡します。

TVSDKは、リスナーを`MediaPlayer`インターフェイス内のパブリック内部インターフェイスとして定義します。

アプリケーションで、アプリケーションに影響を与えるTVSDKイベント用のイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要があるイベントを決定します。

   * 必須イベント:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >プレイヤーのステータスが必要に応じて変化した場合に発生する、ステータス変更イベントをリッスンします。 提供される情報には、プレイヤーが次に実行できる操作に影響する可能性のあるエラーが含まれます。

   * 使用しているアプリケーションに応じた他のイベントについては、「イベントの概要」を参照してください。

1. 各イベントにイベントリスナーを実装し、追加します。

   >[!NOTE]
   >
   >ほとんどのイベントで、TVSDKはイベントリスナーに引数を渡します。 これらの値は、次に何を行うかを決定する際に役立つイベントに関する情報を提供します。 `MediaPlayerEvent`定義済みリストは、`MediaPlayer`がディスパッチするすべてのイベントをリストします。 詳しくは、「イベントの概要」を参照してください。

   例えば、`mPlayer`が`MediaPlayer`のインスタンスである場合、次のようにイベントリスナーを追加し、構造化します。

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

## 再生イベントの順序{#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づくアクションを期待された順序で実装できます。

次の例は、再生中に発生する一部のイベントの順序を示しています。

`MediaPlayer.replaceCurrentResource`を介してメディアリソースを正常に読み込むと、次の順序でイベントされます。

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.INITIALIZING`

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.INITIALIZED`

>[!TIP]
>
>メインスレッドにメディアリソースを読み込みます。 メディアリソースをバックグラウンドスレッドに読み込むと、この操作またはそれ以降の操作で`MediaPlayerException`などのエラーが発生し、終了する場合があります。

`MediaPlayer.prepareToPlay`を介して再生を準備する場合、イベントの順序は次のとおりです。

1. `MediaPlayerEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.PREPARING`

1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合。
1. `MediaPlayerEvent.STATUS_CHANGED` ステータス  `MediaPlayerStatus.PREPARED`

ライブ/リニアストリームの場合、再生中、再生時間が進み、追加のオポチュニティが解決されると、次の順序でイベントが発生します。

1. `MediaPlayerEvent.ITEM_UPDATED`
1. `MediaPlayerEvent.TIMELINE_UPDATED` 広告が挿入された場合

## 広告イベントの順序{#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

再生に広告が含まれる場合、TVSDKは、通常予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、期待されたシーケンス内のイベントに基づいてアクションを実装できます。

広告を再生する場合、イベントの順序は次のとおりです。

* `MediaPlayerEvent.AD_RESOLUTION_COMPLETE`

次のイベントが、広告の時間内のすべての広告に対してディスパッチされます。

* `MediaPlayerEvent.AD_BREAK_START`
* `MediaPlayerEvent.AD_START`
* `MediaPlayerEvent.AD_PROGRESS (multiple times)`
* `MediaPlayerEvent.AD_CLICK (for each click)`
* `MediaPlayerEvent.AD_COMPLETE`
* `MediaPlayerEvent.AD_BREAK_COMPLETE`

次の例に、広告再生イベントの一般的な流れを示します。

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

## DRMイベントの順序{#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。

DRM関連のイベントをすべて通知するには、`MediaPlayerEvent.DRM_METADATA`をリッスンします。 TVSDKは、追加のDRMイベントを`DRMManager`クラスを通じてディスパッチします。

## ローダイベントの順序{#section_5638F8EDACCE422A9425187484D39DCC}

TVSDKは、ローダのイベントが発生すると`MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE`をディスパッチします。