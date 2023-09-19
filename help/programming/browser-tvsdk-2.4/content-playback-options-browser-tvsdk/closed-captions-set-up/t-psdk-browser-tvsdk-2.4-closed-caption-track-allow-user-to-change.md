---
description: ユーザーがクローズドキャプショントラックを選択する方法の例を以下に示します。
title: ユーザーがトラックを変更できるようにする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---

# ユーザーがトラックを変更できるようにする{#allow-the-user-to-change-the-track}

ユーザーがクローズドキャプショントラックを選択する方法の例を以下に示します。

1. 使用可能なクローズドキャプショントラックを表示するには、 `MediaPlayerItem.closedCaptionsTracks` プロパティ。

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. 現在のクローズドキャプショントラックを設定するには、 `MediaPlayerItem.selectClosedCaptionsTrack` メソッド。
1. メディアプレーヤーアイテムの準備が完了したら、 ` MediaPlayer.  currentItem ` メソッド。

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```
