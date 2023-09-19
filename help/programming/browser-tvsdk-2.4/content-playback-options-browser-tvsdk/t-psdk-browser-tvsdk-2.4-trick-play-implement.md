---
description: メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定する必要があります。
title: 早送りと巻き戻しの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 早送りと巻き戻しの実装{#implement-fast-forward-and-rewind}

メディアを早送りまたは巻き戻しする場合、ユーザーはトリック再生モードになります。 トリック再生モードに入るには、 MediaPlayer の再生速度を 1 以外の値に設定する必要があります。

>[!IMPORTANT]
>
>* トリック再生モードは、MPEG ダッシュおよび HLS VOD コンテンツに対してのみサポートされます。
>* ライブストリームまたは広告では、トリック再生モードはサポートされていません。
>* メインコンテンツから広告に切り替えると、Browser TVSDK はトリック再生モードを終了します。
>

速度を切り替えるには、1 つの値を設定する必要があります。

1. 通常の再生モード (1 x) から、 `MediaPlayer` を使用して、値を設定できます。

   * The `MediaPlayerItem` クラスは、許可される再生レートを定義します。
   * 指定されたレートが許可されていない場合、ブラウザー TVSDK は、許可されている最も近いレートを選択します。

     次の関数の例では、レートを設定します。

     ```js
     setTrickPlayRate = function (player, trickPlayRate) { 
                   player.rate = trickPlayRate; 
     }
     ```

     次の関数の例を使用して、使用可能な再生速度を問い合わせることができます。

     ```js
     getAvailableTrickPlayRates = function (player) { 
              var item = player.currentItem; 
              var availableRates = item. availablePlaybackRates; 
              return availableRates; 
     } 
     ```

1. オプションで、レート変更イベントをリッスンできます。このイベントを使用して、レート変更のリクエストを行った日時や、レート変更が実際に発生した日時を通知できます。

       ブラウザー TVSDK は、トリック再生に関連する以下のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` 時に `rate` の値が別の値に変更された場合。

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` 選択した速度で再生が再開されたとき。

     ブラウザー TVSDK は、プレーヤーがトリック再生モードから通常再生モードに戻ると、これらの両方のイベントをディスパッチします。

## レート変更 API 要素 {#rate-change-API-elements}

ブラウザー TVSDK には、有効な率、現在の率、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を決定するメソッド、プロパティ、イベントが含まれています。

再生率を変更するには、次の API 要素を使用します。

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates`  — 有効なレートを指定します。

  | レート値 | 再生時の効果 |
  |---|---|
  | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | 指定した乗数が通常よりも速い早送りモードに切り替えます（たとえば、4 は通常より 4 倍も速い）。 |
  | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | 早戻しモードに切り替えます。 |
  | 1.0 | 通常の再生モードに切り替えます ( `play` は、 rate プロパティを 1.0 に設定するのと同じです )。 |
  | 0.0 | 一時停止（呼び出し） `pause` は、 rate プロパティを 0.0 に設定する場合と同じです )。 |

## トリック再生の制限事項と動作 {#limitations-and-behavior-trick-play}

トリック再生モードの動作には、いくつかの制限事項があり、いくつかの問題があります。

トリック再生モードの制限のリストを次に示します。

* ストリームにトリック再生適応が含まれていない場合、早戻しは無効になり、早送りの最大再生率は 8 に制限されます。
* トリック再生アダプティブを使用してトリックモードを提供すると、オーディオトラックは無効になります。
* トリック再生モードでは、オーディオおよびクローズドキャプショントラックの切り替えが無効になります。
* 再生と一時停止が有効になっています。
* シーク時に、再生がトリック再生モードの場合、再生レートが 1 に設定され、通常の再生が再開されます。
* 可変ビットレート (ABR) ロジックが有効になっています。

  通常のアダプティブを使用する場合、プロファイルは `ABRControlParameters.minBitRate` および `ABRControlParameters.maxBitRate`. トリック再生アダプテーションを使用する場合、プロファイルは `ABRControlParameters.minTrickPlayBitRate` および `ABRControlParameters.maxTrickPlayBitRate`.
