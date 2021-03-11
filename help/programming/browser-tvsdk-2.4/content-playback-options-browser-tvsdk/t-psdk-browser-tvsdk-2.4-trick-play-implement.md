---
description: メディアを早送りまたは巻き戻しする場合は、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定する必要があります。
title: 早送りと巻き戻しの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# 早送りと巻き戻しの実装{#implement-fast-forward-and-rewind}

メディアを早送りまたは巻き戻しする場合は、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定する必要があります。

>[!IMPORTANT]
>
>* トリック再生モードは、MPEG DashおよびHLS VODコンテンツに対してのみサポートされています。
>* トリック再生モードは、ライブストリームまたは広告に対してはサポートされていません。
>* メインコンテンツから広告に切り替えると、ブラウザーTVSDKはトリック再生モードを終了します。

>



速度を切り替えるには、1つの値を設定する必要があります。

1. `MediaPlayer`の速度を許可値に設定して、通常再生モード(1x)からトリック再生モードに移行します。

   * `MediaPlayerItem`クラスは、許可される再生速度を定義します。
   * 指定されたレートが許可されていない場合、ブラウザーTVSDKは、許可されている最も近いレートを選択します。

      次に示す関数の例では、レートを設定します。

      ```js
      setTrickPlayRate = function (player, trickPlayRate) { 
                    player.rate = trickPlayRate; 
      }
      ```

      次の関数の例を使用して、使用可能な再生速度をクエリできます。

      ```js
      getAvailableTrickPlayRates = function (player) { 
               var item = player.currentItem; 
               var availableRates = item. availablePlaybackRates; 
               return availableRates; 
      } 
      ```

1. 必要に応じてレート変更イベントをリッスンできます。これにより、レート変更を要求したときやレート変更が実際に発生したときに通知されます。

       ブラウザーTVSDKは、トリック再生に関連する次のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` の値が別の `rate` 値に変更された場合。

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` 選択した速度で再生が再開されたとき。

      ブラウザーTVSDKは、プレイヤーがトリック再生モードから通常再生モードに戻ると、これらの両方のイベントをディスパッチします。

## レート変更API要素{#rate-change-API-elements}

ブラウザーTVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関するその他の機能を決定するためのメソッド、プロパティ、イベントが含まれています。

再生率を変更するには、次のAPIエレメントを使用します。

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates`  — 有効な料金を指定します。

   | レート値 | 再生への影響 |
   |---|---|
   | 2.0、4.0、8.0、16.0、32.0、64.0 | 指定した倍速の早送りモードに切り替えます（例えば、4は4倍速です）。 |
   | -2.0、-4.0、-8.0、-16.0、-32.0、-64.0 | 早戻しモードに切り替えます。 |
   | 1.0 | 通常再生モードに切り替えます（`play`を呼び出すのと、rateプロパティを1.0に設定するのは同じことです）。 |
   | 0.0 | 一時停止します（`pause`を呼び出すのと、レートプロパティを0.0に設定するのは同じことです）。 |

## トリック再生の制限事項と動作{#limitations-and-behavior-trick-play}

トリック再生モードの動作には、いくつかの制限事項といくつかの問題があります。

トリック再生モードの制限のリストを次に示します。

* ストリームにトリック再生の適応が含まれていない場合、早戻しは無効になり、早送りの最大再生率は8に制限されます。
* トリック再生アダプティブを使用してトリックモードを提供する場合、オーディオトラックは無効になります。
* トリック再生モードでは、オーディオトラックとクローズドキャプショントラックの切り替えは無効になります。
* 再生と一時停止が有効です。
* シーク時に、再生がトリック再生モードの場合、再生レートは1に設定され、通常の再生が再開されます。
* 可変ビットレート(ABR)ロジックが有効です。

   通常のアダプティブを使用する場合、プロファイルは`ABRControlParameters.minBitRate`と`ABRControlParameters.maxBitRate`の間で制限されます。 トリック再生アダプティブを使用する場合、プロファイルは`ABRControlParameters.minTrickPlayBitRate`と`ABRControlParameters.maxTrickPlayBitRate`の間で制限されます。