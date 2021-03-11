---
description: クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替えたり、形式設定を選択したりできます。
title: クローズドキャプションを公開する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---


# クローズドキャプションを公開する{#expose-closed-captions}

クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替えたり、形式設定を選択したりできます。

クローズドキャプションを公開するには：

1. `PTMediaPlayer`オブジェクトに`closedCaptionDisplayEnabled`プロパティを設定します。

   ユーザーがクローズドキャプションを有効にしている場合、この手順でテキストを表示します。

   >[!NOTE]
   >
   >クライアントユーザーは、iOSアクセシビリティ設定を使用してクローズドキャプションのオン/オフを切り替えます。これらの設定には、フォーマットオプションも含まれます。

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` プロパティは非推奨です。`PTMediaPlayerItem`の`subtitlesOptions`プロパティを使用します。 クローズドキャプションを使用するには、[サブタイトル](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md)を公開するを参照してください。