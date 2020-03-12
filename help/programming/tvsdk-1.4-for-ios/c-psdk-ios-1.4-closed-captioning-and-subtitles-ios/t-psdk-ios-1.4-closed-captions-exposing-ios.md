---
description: クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替え、書式を選択できます。
seo-description: クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替え、書式を選択できます。
seo-title: クローズドキャプションの公開
title: クローズドキャプションの公開
uuid: 209b34ca-f14e-499e-af5f-2d8c7b359ef8
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b

---


# クローズドキャプションの公開 {#expose-closed-captions}

クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替え、書式を選択できます。

クローズドキャプションを公開するには：

1. オブジェクト `PTMediaPlayer` 内で、プロパティを設定 `closedCaptionDisplayEnabled` します。

   ユーザーがクローズドキャプションを有効にしている場合、この手順でテキストを表示します。

   >[!NOTE]
   >
   >クライアントユーザーは、iOSのアクセシビリティ設定を使用してクローズドキャプションのオン/オフを切り替えます。また、これらの設定には、形式オプションも含まれます。

   >[!NOTE]
   >
   >`closedCaptionDisplayEnabled` プロパティは非推奨です。 のプロパ `subtitlesOptions` ティを使用し `PTMediaPlayerItem`ます。 クローズドキ [ャプションを使用するには](../../tvsdk-1.4-for-ios/c-psdk-ios-1.4-closed-captioning-and-subtitles-ios/t-psdk-ios-1.4-subtitles-exposing-ios.md) 、サブタイトルを公開するを参照してください。