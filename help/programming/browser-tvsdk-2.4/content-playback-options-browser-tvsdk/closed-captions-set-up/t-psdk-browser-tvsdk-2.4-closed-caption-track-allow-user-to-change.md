---
description: 以下に、クローズドキャプショントラックを選択する方法の例を示します。
seo-description: 以下に、クローズドキャプショントラックを選択する方法の例を示します。
seo-title: ユーザーがトラックを変更できるようにする
title: ユーザーがトラックを変更できるようにする
uuid: bd3d4d20-9b52-4365-b656-83ec2a405a1c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ユーザーがトラックを変更できるようにする{#allow-the-user-to-change-the-track}

以下に、クローズドキャプショントラックを選択する方法の例を示します。

1. 使用可能なクローズドキャプショントラックを表示するには、プロパティを使 `MediaPlayerItem.closedCaptionsTracks` 用します。

   ```js
   var tracks = item.closedCaptionsTracks;
   ```

1. 現在のクローズドキャプショントラックを設定するには、このメソッドを使用 `MediaPlayerItem.selectClosedCaptionsTrack` します。
1. メディアプレイヤーアイテムを準備したら、このメソッドを使用して、メディアプレイヤーからアイテムを取得 ` MediaPlayer.  currentItem ` します。

   ```js
   // Select the cc track with index k. 
   var item = mediaPlayer.currentItem;     
   var tracks = item.closedCaptionsTracks; 
   
   if (k >= 0 && k < tracks.length) { 
       item.selectClosedCaptionsTrack(tracks[k]); 
   }
   ```

