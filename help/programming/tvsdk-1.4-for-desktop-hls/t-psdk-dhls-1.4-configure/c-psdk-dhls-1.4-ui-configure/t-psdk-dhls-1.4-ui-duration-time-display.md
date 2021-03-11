---
description: TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。
title: ビデオの長さ、現在時間および残り時間の表示
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# ビデオの長さ、現在時間、残り時間の表示{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDKを使用して、シークバーに表示できるメディアに関する情報を取得できます。

1. プレイヤーがINITIALIZED状態になるまで待ちます。
1. `MediaPlayer.currentTime`プロパティを使用して、再生ヘッドの現在の時間を取得します。

   これは、仮想タイムライン上の再生ヘッドの現在の位置をミリ秒単位で返します。 時間は、メインストリームにスライスされる複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある、解決済みストリームを基準にして計算されます。 ライブ/リニアストリームの場合、戻り時間は常に再生時間の範囲にあります。

   ```
   function get currentTime():Number;
   ```

1. ストリームの再生範囲を取得し、長さを決定します。
   1. `mediaPlayer.playbackRange`プロパティを使用して、仮想タイムラインの時間範囲を取得します。

      ```
      function get playbackRange():TimeRange;
      ```

   1. `mediacore.utils.TimeRange`を使用して時間範囲を解析します。
   1. 長さを調べるには、範囲の終わりから開始を引きます。

      これには、ストリームに挿入される追加コンテンツ（広告）の長さも含まれます。

      VODの場合、範囲は常に0で始まり、終了値はメインコンテンツの長さと、ストリームに挿入される追加コンテンツ（広告）の長さの合計と等しくなります。

      リニア/ライブアセットの場合、範囲は再生時間の範囲を表し、再生中にこの範囲が変わります。

      TVSDKは、`MediaPlayerItemEvent.ITEM_UPDATED`イベントをディスパッチして、メディア項目がリフレッシュされ、その属性（再生範囲を含む）が更新されたことを示します。

1. `MediaPlayer`で使用できるメソッドと、FlexSDKでpublicクラスとして使用可能な`HSlider`クラスを使用して、シークバーパラメーターを設定します。

1. タイマーを使用して、定期的に現在時間を取得し、`SeekBar`を更新します。
