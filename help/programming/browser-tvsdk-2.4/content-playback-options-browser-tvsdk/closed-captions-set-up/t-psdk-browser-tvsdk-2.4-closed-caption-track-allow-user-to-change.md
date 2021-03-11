---
description: 以下は、クローズドキャプショントラックの選択方法の例です。
title: ユーザーがトラックを変更できるようにする
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# ユーザーがトラック{#allow-the-user-to-change-the-track}を変更できるようにします

以下は、クローズドキャプショントラックの選択方法の例です。

1. 使用可能なクローズドキャプショントラックを表示するには、`MediaPlayerItem.closedCaptionsTracks`プロパティを使用します。

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. 現在のクローズドキャプショントラックを設定するには、`MediaPlayerItem.selectClosedCaptionsTrack`メソッドを使用します。
1. メディアプレイヤーアイテムを準備したら、` MediaPlayer.  currentItem `メソッドを使用して、メディアプレイヤーからアイテムを取得します。

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

