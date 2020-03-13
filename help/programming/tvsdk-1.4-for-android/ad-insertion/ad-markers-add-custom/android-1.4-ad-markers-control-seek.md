---
description: カスタム広告マーカーを使用する場合、TVSDKが広告をシークする方法のデフォルトの動作を上書きできます。
seo-description: カスタム広告マーカーを使用する場合、TVSDKが広告をシークする方法のデフォルトの動作を上書きできます。
seo-title: カスタム広告マーカーのシークオーバーの再生動作の制御
title: カスタム広告マーカーのシークオーバーの再生動作の制御
uuid: cf973caf-be29-46ce-bfa4-651e7653f8d4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# カスタム広告マーカーのシークオーバーの再生動作の制御{#control-playback-behavior-for-seeking-over-custom-ad-markers}

カスタム広告マーカーを使用する場合、TVSDKが広告をシークする方法のデフォルトの動作を上書きできます。

デフォルトでは、ユーザーがカスタム広告マーカーの配置から生じる広告セクションをシークインまたはシークパストすると、TVSDKは広告をスキップします。 これは、標準の広告の時間の現在の再生動作と異なる場合があります。

ユーザーが1つ以上のカスタム広告をシークパストしたときに、最も最近スキップされたカスタム広告の先頭に再生ヘッドを再配置するようTVSDKに指示できます。

1. 列挙値が文字列値「true」(ブ `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` ール値ではなく)に設定されたメタデータインスタンスを設定し `true`ます。

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. インスタンスを作成し、 `MediaResource` に追加の設定オプションを渡して設定しま `TimeRangeCollection.toMetadata`す。 このメソッドは、別の汎用メタデータ構造を介して追加の設定オプションを受け取ります。

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```

