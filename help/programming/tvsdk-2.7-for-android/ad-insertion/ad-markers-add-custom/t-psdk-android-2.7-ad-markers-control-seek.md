---
description: カスタム広告マーカーを使用する場合、TVSDKが広告をスキップするシークをどのように処理するかに関するデフォルトの動作を上書きできます。
seo-description: カスタム広告マーカーを使用する場合、TVSDKが広告をスキップするシークをどのように処理するかに関するデフォルトの動作を上書きできます。
seo-title: カスタム広告マーカーのシークオーバーの再生動作の制御
title: カスタム広告マーカーのシークオーバーの再生動作の制御
uuid: 248e914e-81b7-4aa5-a4d5-06ca2666e006
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# カスタム広告マーカーのシークオーバーの再生動作の制御 {#control-playback-behavior-for-seeking-over-custom-ad-markers}

カスタム広告マーカーを使用する場合、TVSDKが広告をスキップするシークをどのように処理するかに関するデフォルトの動作を上書きできます。

デフォルトでは、ユーザーがカスタム広告マーカーの配置から生じる広告セクションをシークインまたはシークパストすると、TVSDKは広告をスキップします。 これは、標準の広告の時間の現在の再生動作と異なる場合があります。 TVSDKは、ユーザーが1つ以上のカスタム広告をシークパストしたときに、最も最近スキップされたカスタム広告の先頭に再生ヘッドを再配置するように設定できます。

1. 電話を `CustomRangeMetadata.setAdjustSeekPosition` して `true`。

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. でを使 `customRangeMetadata` 用しま `MediaPlayerItemConfig`す。

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```

