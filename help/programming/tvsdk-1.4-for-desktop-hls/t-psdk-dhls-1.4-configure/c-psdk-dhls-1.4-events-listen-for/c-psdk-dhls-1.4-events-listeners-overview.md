---
description: TVSDK のイベントは、プレーヤーの状態、発生するエラー、再生を開始するビデオなど、リクエストしたアクションの完了、広告完了など、暗黙的に発生するアクションを示します。
title: Primetime Player イベントのリッスン
exl-id: 3a740245-a9e1-4e36-8761-f9f4b4e85b93
source-git-commit: 3bbf70e07b51585c9b53f470180d55aa7ac084bc
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 概要 {#implement-event-listeners-and-callbacks-overview}

イベントハンドラーを使用すると、 TVSDK はイベントに応答できます。 イベントが発生すると、 TVSDK のイベントメカニズムが登録されたイベントハンドラーを呼び出し、イベント情報をハンドラーに渡します。

Flashランタイムは、一連のカスタムイベントを使用および定義する汎用のイベントメカニズムを提供します。 アプリケーションは、アプリケーションに影響を与える TVSDK イベント用のイベントリスナーを実装する必要があります。

1. アプリケーションがリッスンするイベントを決定します。

   * **必須イベント**:すべての再生イベントをリッスンします。

      >[!IMPORTANT]
      >
      >再生イベント `MediaPlayerStatusChangeEvent.STATUS_CHANGE` は、エラーを含むプレーヤーのステータスを示します。 どの状態も、プレーヤーの次のステップに影響を与える可能性があります。

   * **その他のイベント**:アプリケーションに応じて、オプションです。

      例えば、再生に広告を組み込む場合は、すべての `AdBreakPlaybackEvent` イベントと `AdPlaybackEvent` イベントをリッスンします。

1. 各イベントのイベントリスナーを実装します。

   TVSDK は、イベントリスナーコールバックにパラメーター値を返します。 これらの値は、適切なアクションを実行するためにリスナーで使用できるイベントに関する関連情報を提供します。

   `Event` クラスは、すべてのコールバックインターフェイスをリストします。 各インターフェイスには、そのインターフェイスに対して返されるパラメータが表示されます。

   例：

   ```
   public function MediaPlayerStatusChangeEvent(type:String,  
                   bubbles:Boolean = false,  
                   cancelable:Boolean = false,  
                   status:String = null,  
                   error:MediaError = null) 
   ```

1. `MediaPlayer.addEventListener` を使用して、`MediaPlayer` オブジェクトにコールバックリスナーを登録します。

   `MediaPlayer` は、 `flash.events.IEventDispatcher`Player のコアファイルの一部で、関数と関数を含むFlashを拡 `addEventListener` 張しま `removeEventListener`す。

   ```
   mediaPlayer.addEventListener( 
     MediaPlayerStatusChangeEvent.STATUS_CHANGED,  
     onStatusChanged);
   ```
