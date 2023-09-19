---
description: カスタム広告マーカーを使用する際に、 TVSDK が広告を介したシークを処理する方法に関するデフォルトの動作を上書きできます。
title: カスタム広告マーカーのシークオーバーに対する再生動作の制御
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# カスタム広告マーカーのシークオーバーに対する再生動作の制御 {#control-playback-behavior-for-seeking-over-custom-ad-markers}

カスタム広告マーカーを使用する際に、 TVSDK が広告を介したシークを処理する方法に関するデフォルトの動作を上書きできます。

デフォルトでは、ユーザーがカスタム広告マーカーを配置した広告セクションをシークインまたはシークパストする場合、 TVSDK は広告をスキップします。 これは、標準の広告の時間に関する現在の再生動作とは異なる場合があります。 ユーザーが 1 つ以上のカスタム広告をシークパストする際に、再生ヘッドを最近スキップしたカスタム広告の先頭に再配置するように TVSDK を設定できます。

1. 通話 `CustomRangeMetadata.setAdjustSeekPosition` 次を使用 `true`.

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. 用途 `customRangeMetadata` in `MediaPlayerItemConfig`.

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
