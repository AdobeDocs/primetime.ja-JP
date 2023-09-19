---
description: TVSDK からのイベントは、プレーヤーの状態、発生するエラー、再生を開始するビデオなど、リクエストしたアクションの完了、広告の完了など、暗黙的に発生するアクションの完了を示します。
title: Primetime Player イベントのリッスン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 概要 {#implement-event-listeners-and-callbacks-overview}

イベントハンドラーを使用すると、 TVSDK はイベントに応答できます。 イベントが発生すると、 TVSDK のイベントメカニズムは登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

Flashランタイムは、汎用のイベントメカニズムを提供します。 TVSDK は、このメカニズムを使用して、一連のカスタムイベントを定義します。 アプリケーションは、アプリケーションに影響を与える TVSDK イベント用のイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンする必要のあるイベントを決定します。

   * **必須イベント**：すべての再生イベントをリッスンします。

     >[!IMPORTANT]
     >
     >再生イベント `MediaPlayerStatusChangeEvent.STATUS_CHANGE` は、エラーを含むプレーヤーのステータスを示します。 どの状態も、プレーヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**：アプリケーションに応じて、オプションです。

     例えば、再生に広告を組み込む場合は、 `AdBreakPlaybackEvent` および `AdPlaybackEvent` イベント。

1. 各イベントのイベントリスナーを実装します。

   TVSDK は、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   The `Event` クラスは、すべてのコールバックインターフェイスをリストします。 各インターフェイスには、そのインターフェイスに対して返されるパラメータが表示されます。

   例：

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. コールバックリスナーを `MediaPlayer` 使用してオブジェクトを `MediaPlayer.addEventListener`.

   `MediaPlayer` extends `flash.events.IEventDispatcher`:Flashプレーヤーのコアファイルの一部で、関数を含みます。 `addEventListener` および `removeEventListener`.

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```
