---
description: カスタム広告マーカーを使用する場合、TVSDKが広告をスキップする方法に関するデフォルトの動作を上書きできます。
seo-description: カスタム広告マーカーを使用する場合、TVSDKが広告をスキップする方法に関するデフォルトの動作を上書きできます。
seo-title: カスタム広告マーカーのシークオーバーに対する再生動作の制御
title: カスタム広告マーカーのシークオーバーに対する再生動作の制御
uuid: cf973caf-be29-46ce-bfa4-651e7653f8d4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# カスタム広告マーカー{#control-playback-behavior-for-seeking-over-custom-ad-markers}をシークオーバーした場合の再生動作の制御

カスタム広告マーカーを使用する場合、TVSDKが広告をスキップする方法に関するデフォルトの動作を上書きできます。

デフォルトでは、ユーザーが、カスタム広告マーカーを配置した広告セクションをシークインまたはシークパストすると、TVSDKは広告をスキップします。 これは、標準的な広告の時間の現在の再生動作と異なる場合があります。

ユーザーが1つ以上のカスタム広告をシークパストする場合に、最も最近スキップされたカスタム広告の先頭に再生ヘッドを再配置するようTVSDKに指示できます。

1. `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED`定義済みリストを文字列値&quot;true&quot;に設定して（ブール値`true`ではなく）、メタデータインスタンスを設定します。

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. `MediaResource`インスタンスを作成し、設定します。追加の設定オプションを`TimeRangeCollection.toMetadata`に渡します。 このメソッドは、別の汎用メタデータ構造体を介して追加の設定オプションを受け取ります。

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```

