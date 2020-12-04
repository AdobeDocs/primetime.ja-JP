---
description: 以下は、クローズドキャプショントラックの選択方法の例です。
seo-description: 以下は、クローズドキャプショントラックの選択方法の例です。
seo-title: ユーザーがトラックを変更できるようにする
title: ユーザーがトラックを変更できるようにする
uuid: bd3d4d20-9b52-4365-b656-83ec2a405a1c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '97'
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

