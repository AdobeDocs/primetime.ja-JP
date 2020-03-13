---
description: TVSDKのイベントは、プレイヤーの状態、発生したエラー、再生を開始するビデオ、広告完了など、要求したアクションの完了、暗黙的に発生したアクションを示します。
seo-description: TVSDKのイベントは、プレイヤーの状態、発生したエラー、再生を開始するビデオ、広告完了など、要求したアクションの完了、暗黙的に発生したアクションを示します。
seo-title: Primetime Playerイベントのリッスン
title: Primetime Playerイベントのリッスン
uuid: e72782bf-9d26-4285-85e4-fd4d803c1bbe
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40

---


# 概要 {#implement-event-listeners-and-callbacks-overview}

イベントハンドラーを使用すると、TVSDKはイベントに応答できます。 イベントが発生すると、TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

Flash Runtimeは汎用のイベントメカニズムを提供します。TVSDKは、このメカニズムを使用し、一連のカスタムイベントを定義します。 アプリケーションは、アプリケーションに影響を与えるTVSDKイベントのイベントリスナーを実装する必要があります。

ビデオ分析のイベントの完全なリストについては、コアビデオ再生の追跡 [を参照してください](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html)。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必要なイベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベントは、エ `MediaPlayerStatusChangeEvent.STATUS_CHANGE` ラーを含むプレイヤーのステータスを提供します。 どの状態でも、プレイヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、再生に広告を組み込む場合は、すべてのイベントとイベントをリス `AdBreakPlaybackEvent` ンし `AdPlaybackEvent` ます。

1. 各イベントのイベントリスナーを実装します。

   TVSDKは、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   このクラス `Event` は、すべてのコールバックインターフェイスをリストします。 各インターフェイスには、そのインターフェイスに対して返されるパラメータが表示されます。

   例：

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. を使用して、コールバックリスナーをオブジ `MediaPlayer` ェクトに登録しま `MediaPlayer.addEventListener`す。

   `MediaPlayer` は、Flash `flash.events.IEventDispatcher`Playerのコアファイルの一部で、関数と関数を含む拡張子 `addEventListener` です `removeEventListener`。

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


