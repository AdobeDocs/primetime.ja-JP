---
description: イベントハンドラーを使用すると、 TVSDK はイベントに応答できます。
title: イベントリスナーとコールバックの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# イベントリスナーとコールバックの実装{#implement-event-listeners-and-callbacks}

イベントハンドラーを使用すると、 TVSDK はイベントに応答できます。

イベントが発生すると、 TVSDK のイベントメカニズムは登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

TVSDK は、リスナーを、 `MediaPlayer` インターフェイス。

アプリケーションは、アプリケーションに影響を与える TVSDK イベント用のイベントリスナーを実装する必要があります。

ビデオ分析のイベントの完全なリストについては、コアビデオ再生の追跡を参照してください。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必須イベント**：すべての再生イベントをリッスンします。

     >[!IMPORTANT]
     >
     >再生イベント `onStateChanged` は、エラーを含むプレーヤーの状態を示します。 どの状態も、プレーヤーの次のステップに影響を与える可能性があります

   * **その他のイベント**：アプリケーションに応じて、オプションです。

     例えば、再生に広告を組み込む場合は、 AdPlaybackEventListener コールバックを実装します。

1. 各イベントのイベントリスナーを実装します。

   TVSDK は、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   `MediaPlayer.EventListener` すべてのコールバックインターフェイスをリストします。 各インターフェイスには、各イベントに対して返されるコールバック名とパラメーターが表示されます。

   例：

   ```
   MediaPlayer.PlaybackEventListener.onStateChanged( 
    MediaPlayer.PlayerState state, MediaPlayerNotification notification)
   ```

1. コールバックリスナーを `MediaPlayer` 使用してオブジェクトを `MediaPlayer.addEventListener`.

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

TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

次の例は、再生イベントを含む一部のイベントの順序を示しています。

* を介してメディアリソースを正常に読み込んだ場合 `MediaPlayer.replaceCurrentResource`の場合、イベントの順序は次のとおりです。

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持つ `MediaPlayer.PlayerState.INITIALIZING`

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持つ `MediaPlayer.PlayerState.INITIALIZED`

>[!TIP]
>
>メディアリソースをメインスレッドに読み込みます。 メディアリソースをバックグラウンドスレッドに読み込むと、この操作または後続の TVSDK 操作、あるいはその両方で、エラー ( 例えば、 `IllegalStateException`) をクリックして終了します。

* を使用して再生を準備する場合 `MediaPlayer.prepareToPlay`の場合、イベントの順序は次のとおりです。

1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持つ `MediaPlayerStatus.PREPARING`

1. `MediaPlayer.PlaybackEventListener.onTimelineUpdated` 広告が挿入された場合。
1. `MediaPlayer.PlaybackEventListener.onStateChanged` 状態を持つ `MediaPlayerStatus.PREPARED`

* ライブ/リニアストリームの場合、再生中に、再生ウィンドウが進み、追加のオポチュニティが解決されると、イベントの順序は次のようになります。

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

再生に広告が含まれている場合、 TVSDK は、一般に予想されるシーケンスでイベント/通知をディスパッチします。 プレーヤーでは、予想されるシーケンス内のイベントに基づいてアクションを実装できます。

広告を再生する際のイベントの順序は次のとおりです。

* `AdPlaybackEventListener.onAdBreakStart`
* 広告ブレークの各広告に対して、次の情報がディスパッチされます。

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` （広告の再生中に複数回）
   * `AdPlaybackEventListener.onAdClick` （クリックごと）
   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdBreakComplete`

次の例に、広告再生イベントの一般的な進行を示します。

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

広告を再生する際のイベントの順序は次のとおりです。

* `AdPlaybackEventListener.onAdBreakStart`
* 広告ブレークの各広告に対して、次の情報がディスパッチされます。

   * `AdPlaybackEventListener.onAdStart`
   * `AdPlaybackEventListener.onAdProgress` （広告の再生中に複数回）
   * `AdPlaybackEventListener.onAdClick` （クリックごと）
   * `AdPlaybackEventListener.onAdStart`

* `AdPlaybackEventListener.onAdBreakComplete`

次の例に、広告再生イベントの一般的な進行を示します。

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

## QoS イベント {#section_9BFF3CD7AA1C4BD6960ACF6B9C0B25CC}

TVSDK は、サービス品質 (QoS) イベントをディスパッチして、バッファリングやシークイベントなど、QoS 統計の計算に影響を与える可能性のあるイベントについてアプリケーションに通知します。

次の例に、これらのイベントの一般的な流れを示します。

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

## DRM イベント {#section_3FECBF127B3E4EFEAB5AE87E89CCDE7C}

TVSDK は、新しい DRM メタデータが使用可能になったときなど、DRM 関連の操作に応じて、デジタル著作権管理 (DRM) イベントをディスパッチします。 プレーヤーは、これらのイベントに応じてアクションを実装できます。

DRM 関連のすべてのイベントに関する通知を受け取るには、 `onDRMMetadata(DRMMetadataInfo drmMetadataInfo)`. TVSDK は、 `DRMManager` クラス。

次の例に、一般的な進行状況を示します。

```
mediaPlayer.addEventListener(MediaPlayer.Event.DRM, 
 new MediaPlayer.DRMEventListener() { 
 @Override 
 public void onDRMMetadata(byte[] data, int length, long timestamp) {...} 
}); 
```

## Loader イベント {#section_5638F8EDACCE422A9425187484D39DCC}

プレーヤーでは、次のイベントに基づいてアクションを実装できます。

| イベント | 意味 |
|---|---|
| `onLoadComplete (mediaPlayerItem playerItem)` | メディアリソースの読み込みが正常に完了しました。 |
| `onError` | メディアリソースの読み込み中に問題が発生しました。 |
