---
description: カスタム広告マーカーを使用する場合、TVSDKが広告をスキップするシークをどのように処理するかに関するデフォルトの動作を上書きできます。
title: カスタム広告マーカーのシークオーバーに対する再生動作の制御
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# カスタム広告マーカーをシークオーバーした場合の再生動作の制御{#control-playback-behavior-for-seeking-over-custom-ad-markers}

カスタム広告マーカーを使用する場合、TVSDKが広告をスキップするシークをどのように処理するかに関するデフォルトの動作を上書きできます。

デフォルトでは、ユーザーが、カスタム広告マーカーを配置した広告セクションをシークインまたはシークパストすると、TVSDKは広告をスキップします。 これは、標準的な広告の時間の現在の再生動作と異なる場合があります。 TVSDKは、ユーザーが1つ以上のカスタム広告をシークパストしたときに、最も最近スキップされたカスタム広告の先頭に再生ヘッドを再配置するように設定できます。

1. `CustomRangeMetadata.setAdjustSeekPosition`を`true`で呼び出します。

   ```java
   customRangeMetadata.setAdjustSeekPosition (true);
   ```

1. `MediaPlayerItemConfig`で`customRangeMetadata`を使用します。

   ```java
   // Set customRangeMetadata 
   config.setCustomRangeMetadata(customRangeMetadata); 
   
   // prepare the content for playback by calling replaceCurrentResource 
   mediaPlayer.replaceCurrentResource(mediaResource, config); 
   ```
