---
description: イベントハンドラーを使用すると、TVSDKはイベントに応答できます。
seo-description: イベントハンドラーを使用すると、TVSDKはイベントに応答できます。
seo-title: イベントリスナーとコールバックの実装
title: イベントリスナーとコールバックの実装
uuid: 6b7859a4-55f9-48b1-b1f1-7b79bc92610a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# イベントリスナーとコールバックの実装{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、TVSDKはイベントに応答できます。

イベントが発生すると、TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

TVSDKは、リスナーをインターフェイスのパブリック内部インターフェイスとして定義 `MediaPlayer` します。

アプリケーションは、アプリケーションに影響を与えるTVSDKイベントのイベントリスナーを実装する必要があります。

ビデオ分析のイベントの完全なリストについては、コアビデオ再生の追跡を参照してください。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必要なイベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベントは、 `onStateChanged` エラーを含むプレーヤーの状態を提供します。 どの状態でも、プレイヤーの次のステップに影響を与える可能性があります

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、広告を再生に組み込む場合、AdPlaybackEventListenerコールバックを実装します。

1. 各イベントのイベントリスナーを実装します。

   TVSDKは、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   `MediaPlayer.EventListener` に、すべてのコールバックインターフェイスを示します。 各インターフェイスには、各イベントに対して返されるコールバック名とパラメータが表示されます。

   例：

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. を使用して、コールバックリスナーをオブジ `MediaPlayer` ェクトに登録しま `MediaPlayer.addEventListener`す。

   ```
   mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, 
    new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onStateChanged( 
    MediaPlayer.PlayerState state, 
    MediaPlayerNotification notification) {...} 
   }
   ```

## 再生イベントの順序 {#section_6D412C33ACE54E9D90DB1DAA9AA30272}

TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* メディアリソースを通じて正常に読み込む `MediaPlayer.replaceCurrentResource`と、イベントの順序は次のとおりです。

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持って `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持って `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>メインスレッドにメディアリソースを読み込みます。 メディアリソースをバックグラウンドスレッドに読み込むと、この操作または後続のTVSDK操作、あるいはその両方の操作で、エラー(例えば、 `IllegalStateException`)が発生して終了する場合があります。

* 通じて再生を準備する場合、 `MediaPlayer.prepareToPlay`イベントの順序は次のとおりです。

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持って `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` 広告が挿入された場合。
1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持って `MediaPlayerStatus.PREPARED`

* ライブ/リニアストリームの場合、再生時間が進み、追加のオポチュニティが解決されるに従って、再生中に、イベントの順序は次のとおりです。

1. `MediaPlayer.PlaybackEventListener.onUpdated`
1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` 広告が挿入された場合
1. `MediaPlayerItemEvent.ITEM_UPDATED`
1. `TimelineEvent.TIMELINE_UPDATED` 広告が挿入された場合

次の例に、イベントの一般的な流れを示します。

```java
mediaPlayer.addEventListener(MediaPlayer.Event.PLAYBACK,  
  new MediaPlayer.PlaybackEventListener() { 
    @Override 
    public void onPrepared() {...} 
    @Override 
    public void onUpdated() {...} 
    @Override 
    public void onPlayStart() {...} 
    @Override 
    public void onPlayComplete() {...} 
    @Override 
    public void onSizeAvailable(long height, long width) {...} 
    @Override 
    public void onStateChanged(MediaPlayer.PlayerState state,  
      MediaPlayerNotification notification) {...} 
});
```

## 広告イベントの順序 {#section_7B3BE3BD3B6F4CF69D81F9CFAC24CAD5}

再生に広告が含まれる場合、TVSDKは、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレイヤーは、イベントに基づいて、期待される順序でアクションを実装できます。

広告を再生する場合、イベントの順序は次のとおりです。

* `AdPlaybackEventListener.onAdBreakStart`
* 広告の時間内のすべての広告に対して、次がディスパッチされます。

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` （広告の再生中に複数回）
   * `AdPlaybackEventListener.onAdClick` （クリックごと）
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

次の例は、広告再生イベントの一般的な流れを示しています。

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

広告を再生する場合、イベントの順序は次のとおりです。

* `AdPlaybackEventListener.onAdBreakStart`
* 広告の時間内のすべての広告に対して、次がディスパッチされます。

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` （広告の再生中に複数回）
   * `AdPlaybackEventListener.onAdClick` （クリックごと）
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

次の例は、広告再生イベントの一般的な流れを示しています。

```java
mediaPlayer.addEventListener(MediaPlayer.Event.AD_PLAYBACK,  
  new MediaPlayer.AdPlaybackEventListener() { 
    @Override  
    public void onAdBreakStart(AdBreak adBreak) { ... } 
    @Override 
    public void onAdStart(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdProgress(AdBreak adBreak, Ad ad, int percentage) { ... }  
    @Override 
    public void onAdComplete(AdBreak adBreak, Ad ad) { ... } 
    @Override 
    public void onAdBreakComplete(AdBreak adBreak) { ... } 
    @Override 
    public void onAdClick(AdBreak adBreak, Ad ad, AdClick adClick) { ... } 
});
```

## QoSイベント {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDKは、サービス品質(QoS)イベントをディスパッチして、QoS統計の計算に影響を与える可能性のあるイベント（バッファリングやシークイベントなど）をアプリケーションに通知します。

次の例は、これらのイベントの一般的な流れを示しています。

```java
mediaPlayer.addEventListener(MediaPlayer.Event.QOS,  
  new MediaPlayer.QOSEventListener(){ 
    //For buffering activity 
    @Override 
    public void onBufferStart() 
    @Override 
    public void onBufferComplete() 
    // For seeking 
    @Override 
    public void onSeekStart() 
    @Override 
    public void onSeekComplete(long adjustedTime) 
    @Override 
    public void onLoadComplete (MediaPlayerItem mediaplayeritem) 
    @Override 
    public void onLoadInfo(LoadInfo loadInfo) 
    @Override 
    public void onOperationFailed(MediaPlayerNotification.Warning warning) 
});
```

## DRMイベント {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDKは、新しいDRMメタデータが使用可能になった場合など、DRM関連の操作に応じて、デジタル著作権管理(DRM)イベントをディスパッチします。 プレイヤーは、これらのイベントに応じてアクションを実装できます。

すべてのDRM関連イベントに関する通知を受け取るには、をリッスンしま `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`す。 TVSDKは、クラスを通じて追加のDRMイベントをディスパッ `DRMManager` チします。

次の例に、一般的な流れを示します。

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## ローダイベント {#section_5638F8EDACCE422A9425187484D39DCC}

プレイヤーは、次のイベントに基づいてアクションを実装できます。

| イベント | 意味 |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | メディアリソースの読み込みが正常に完了しました。 |
| `onError` | メディアリソースの読み込みで問題が発生しました。 |

