---
description: TVSDK を使用して、シークバーに表示できるメディアに関する情報を取得できます。
title: ビデオの長さ、現在時間および残り時間を表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ビデオの長さ、現在時間および残り時間を表示{#display-the-duration-current-time-and-remaining-time-of-the-video}

TVSDK を使用して、シークバーに表示できるメディアに関する情報を取得できます。

1. プレーヤーが INITIALIZED ステータスになるまで待ちます。
1. を使用して、現在の再生ヘッド時間を取得する `MediaPlayer.currentTime` プロパティ。

   これは、仮想タイムライン上の現在の再生ヘッドの位置をミリ秒単位で返します。 時間は、メインストリームにスプライスされる複数の広告や広告の時間など、代替コンテンツの複数のインスタンスを含む可能性がある、解決されたストリームを基準に計算されます。 ライブ/リニアストリームの場合、返される時間は常に再生ウィンドウの範囲にあります。

   ```
   function get currentTime():Number;
   ```

1. ストリームの再生範囲を取得し、時間を決定します。
   1. 以下を使用します。 `mediaPlayer.playbackRange` プロパティを使用して、仮想タイムラインの時間範囲を取得します。

      ```
      function get playbackRange():TimeRange;
      ```

   1. を使用して時間範囲を解析 `mediacore.utils.TimeRange`.
   1. 期間を指定するには、範囲の終わりから開始を引きます。

      これには、ストリームに挿入される追加コンテンツ（広告）の期間が含まれます。

      VOD の場合、範囲は常に 0 で始まり、終了値は、ストリーム（広告）に挿入される追加コンテンツの時間とメインコンテンツの時間の合計に等しくなります。

      リニア/ライブアセットの場合、範囲は再生ウィンドウの範囲を表し、この範囲は再生中に変更されます。

      TVSDK が `MediaPlayerItemEvent.ITEM_UPDATED` イベントを使用して、メディアアイテムが更新され、その属性（再生範囲を含む）が更新されたことを示す。

1. で使用できるメソッドの使用 `MediaPlayer` そして `HSlider` Flex SDK でシークバーパラメーターを設定するために一般的に使用可能なクラス。

1. タイマーを使用して、現在の時間を定期的に取得し、 `SeekBar`.
