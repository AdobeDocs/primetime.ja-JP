---
description: TVSDKのイベントは、プレイヤーの状態、発生するエラー、再生を開始するビデオ、広告の完了など、リクエストしたアクションの完了、暗黙的に発生するアクションを示します。
seo-description: TVSDKのイベントは、プレイヤーの状態、発生するエラー、再生を開始するビデオ、広告の完了など、リクエストしたアクションの完了、暗黙的に発生するアクションを示します。
seo-title: Primetime Playerイベントのリッスン
title: Primetime Playerイベントのリッスン
uuid: e72782bf-9d26-4285-85e4-fd4d803c1bbe
translation-type: tm+mt
source-git-commit: 8ff38bdc1a7ff9732f7f1fae37f64d0e1113ff40
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# 概要{#implement-event-listeners-and-callbacks-overview}

イベントハンドラーを使用すると、TVSDKはイベントに応答できます。 イベントが発生すると、TVSDKのイベントメカニズムは、登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

Flashランタイムには、汎用的なイベントメカニズムが用意されています。このメカニズムは、TVSDKが使用し、一連のカスタムイベントを定義する場合にも使用されます。 アプリケーションは、アプリケーションに影響を与えるTVSDKイベント用のイベントリスナーを実装する必要があります。

ビデオ分析のイベントの完全なリストについては、[コアビデオ再生の追跡](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/c_vhl_track-core-vid-playback.html)を参照してください。

1. アプリケーションがリッスンする必要があるイベントを決定します。

   * **必須イベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベント`MediaPlayerStatusChangeEvent.STATUS_CHANGE`は、エラーを含むプレイヤーのステータスを提供します。 状態によっては、プレイヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、再生に広告を組み込む場合は、すべての`AdBreakPlaybackEvent`および`AdPlaybackEvent`イベントをリッスンします。

1. 各イベントにイベントリスナーを実装します。

   TVSDKは、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、リスナーで使用して適切なアクションを実行できるイベントに関する関連情報を提供します。

   `Event`クラスは、すべてのコールバックインターフェイスをリストします。 各インターフェイスには、そのインターフェイスに対して返されるパラメーターが表示されます。

   例：

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. `MediaPlayer.addEventListener`を使用して、`MediaPlayer`オブジェクトにコールバックリスナーを登録します。

   `MediaPlayer` は、 `flash.events.IEventDispatcher`Flashプレーヤーのコアファイルの一部で、関数 `addEventListener` と関数を含み `removeEventListener`ます。

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```


