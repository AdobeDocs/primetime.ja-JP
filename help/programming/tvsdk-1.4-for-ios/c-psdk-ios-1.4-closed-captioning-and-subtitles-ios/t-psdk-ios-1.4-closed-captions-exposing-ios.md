---
description: クライアントプレーヤーでクローズドキャプションを使用できるようにするには、クローズドキャプションを有効にする必要があります。 クローズドキャプションのオン/オフを切り替えたり、書式設定を選択したりできます。
title: クローズドキャプションを公開する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 0%

---

# クローズドキャプションを公開する {#expose-closed-captions}

クライアントプレーヤーでクローズドキャプションを使用できるようにするには、クローズドキャプションを有効にする必要があります。 クローズドキャプションのオン/オフを切り替えたり、書式設定を選択したりできます。

クローズドキャプションを公開するには：

1. In `PTMediaPlayer` オブジェクト、 `closedCaptionDisplayEnabled` プロパティ。

   ユーザーがクローズドキャプションを有効にしている場合、この手順ではテキストが表示されます。

   >[!NOTE]
   >
   >クライアントユーザーは、iOSのアクセシビリティ設定を使用してクローズドキャプションのオン/オフを切り替えます。また、これらの設定には書式設定オプションも用意されています。

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` プロパティは非推奨です。 用途 `subtitlesOptions` のプロパティ `PTMediaPlayerItem`. 詳しくは、 [サブタイトルを公開](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) クローズドキャプションを使用する場合。
