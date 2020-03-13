---
description: クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替え、書式を選択できます。
seo-description: クローズドキャプションをクライアントプレーヤーで使用できるようにするには、有効にする必要があります。 クローズドキャプションのオン/オフを切り替え、書式を選択できます。
seo-title: クローズドキャプションの公開
title: クローズドキャプションの公開
uuid: 7057014a-b14a-4790-8f7f-37d7a1fb8194
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

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
   >`closedCaptionDisplayEnabled` プロパティは非推奨です。 のプロパ `subtitlesOptions` ティを使用し `PTMediaPlayerItem`ます。 クローズドキ [ャプションを使用するには](../../../tvsdk-3x-ios-prog/c-ios-closed-captioning-and-subtitles-ios/c-ios-closed-captioning-and-subtitles-reqts-ios/t-ios-subtitles-exposing-ios.md) 、サブタイトルを公開するを参照してください。