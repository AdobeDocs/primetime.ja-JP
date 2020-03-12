---
description: ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定する必要があります。
seo-description: ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定する必要があります。
seo-title: 早送りと巻き戻しの実装
title: 早送りと巻き戻しの実装
uuid: c1992757-d067-4c11-8d08-fec09099476f
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# 早送りと巻き戻しの実装{#implement-fast-forward-and-rewind}

ユーザーがメディアを早送りまたは巻き戻しすると、トリック再生モードになります。 トリック再生モードに入るには、MediaPlayerの再生速度を1以外の値に設定する必要があります。

>[!IMPORTANT]
>
>* トリック再生モードは、MPEG DashおよびHLS VODコンテンツに対してのみサポートされます。
>* トリック再生モードは、ライブストリームまたは広告ではサポートされていません。
>* メインコンテンツから広告に切り替えると、ブラウザーTVSDKはトリック再生モードを終了します。
>



速度を切り替えるには、1つの値を設定する必要があります。

1. レートを許容値に設定して、通常再生モード(1x)からトリック再生モ `MediaPlayer` ードに移動します。

   * クラス `MediaPlayerItem` は、許可される再生速度を定義します。
   * 指定されたレートが許可されていない場合、ブラウザーTVSDKは、許可されている最も近いレートを選択します。

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

1. オプションで、レート変更イベントをリッスンできます。このイベントによって、レート変更をリクエストしたときや、レート変更が実際に発生したときに通知されます。

       ブラウザーTVSDKは、トリック再生に関連する次のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.RATE_SELECTED` 値が別の `rate` 値に変更された場合。

   * `AdobePSDK.PSDKEventType.RATE_PLAYING` 選択した速度で再生が再開されたとき。

      ブラウザーTVSDKは、プレーヤーがトリック再生モードから通常再生モードに戻ると、これらの両方のイベントをディスパッチします。

## レート変更API要素 {#rate-change-API-elements}

ブラウザーTVSDKには、有効な速度、現在の速度、トリック再生がサポートされているかどうか、および早送りと巻き戻しに関連するその他の機能を判断するためのメソッド、プロパティおよびイベントが含まれています。

次のAPIエレメントを使用して、再生率を変更します。

* `MediaPlayer.rate`
* `PlaybackRateEvent.rate`
* `MediaPlayerItem.istrickPlaySupported`
* `MediaPlayerItem.availablePlaybackRates`  — 有効なレートを指定します。

   | レート値 | 再生への影響 |
   |---|---|
   | 2.0, 4.0, 8.0, 16.0, 32.0, 64.0 | 指定した乗数が通常よりも速い早送りモードに切り替えます（例えば、4は通常よりも4倍速い）。 |
   | -2.0, -4.0, -8.0, -16.0, -32.0, -64.0 | 早戻しモードに切り替えます。 |
   | 1.0 | 通常再生モードに切り替えます( `play` 呼び出しは、rateプロパティを1.0に設定するのと同じです)。 |
   | 0.0 | 一時停止(呼び出 `pause` しは、rateプロパティを0.0に設定するのと同じ) |

## トリック再生の制限と動作 {#limitations-and-behavior-trick-play}

トリック再生モードの動作には、いくつかの制限事項といくつかの問題があります。

トリック再生モードの制限を以下に示します。

* ストリームにトリック再生の適応が含まれていない場合、早戻しは無効になり、早送りの最大再生速度は8に制限されます。
* トリック再生アダプティブを使用してトリックモードを提供する場合、オーディオトラックは無効になります。
* トリック再生モードでは、オーディオおよびクローズドキャプショントラックの切り替えが無効になります。
* 再生と一時停止が有効になっています。
* シーク時に、再生がトリック再生モードの場合、再生レートは1に設定され、通常の再生が再開されます。
* 可変ビットレート(ABR)ロジックが有効です。

   通常のアダプティブを使用する場合、プロファイルはとの間で制 `ABRControlParameters.minBitRate` 限されま `ABRControlParameters.maxBitRate`す。 トリック再生アダプティブを使用する場合、プロファイルはとの間で制限 `ABRControlParameters.minTrickPlayBitRate` されま `ABRControlParameters.maxTrickPlayBitRate`す。