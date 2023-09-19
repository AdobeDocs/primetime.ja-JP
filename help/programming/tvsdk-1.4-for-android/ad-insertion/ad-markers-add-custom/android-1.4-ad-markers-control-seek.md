---
description: カスタム広告マーカーを使用する際に、 TVSDK が広告をシークする方法に関するデフォルトの動作を上書きできます。
title: カスタム広告マーカーのシークオーバーに対する再生動作の制御
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# カスタム広告マーカーのシークオーバーに対する再生動作の制御{#control-playback-behavior-for-seeking-over-custom-ad-markers}

カスタム広告マーカーを使用する際に、 TVSDK が広告をシークする方法に関するデフォルトの動作を上書きできます。

デフォルトでは、ユーザーがカスタム広告マーカーを配置した広告セクションをシークインまたはシークパストする場合、 TVSDK は広告をスキップします。 これは、標準の広告の時間に関する現在の再生動作とは異なる場合があります。

ユーザーが 1 つ以上のカスタム広告をシークパストする際に、最近スキップされたカスタム広告の先頭に再生ヘッドを再配置するよう TVSDK に指示できます。

1. を使用したメタデータインスタンスの設定 `DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED` 列挙で、文字列値「true」に設定されます（ブール値ではありません） `true`) をクリックします。

   ```java
   Metadata metadata = new MetadataNode(); 
   metadata.setValue(DefaultMetadataKeys.METADATA_KEY_ADJUST_SEEK_ENABLED.getValue(),"true");
   ```

1. の作成と設定 `MediaResource` インスタンス、追加の設定オプションをに渡す `TimeRangeCollection.toMetadata`. このメソッドは、別の汎用メタデータ構造を介して追加の設定オプションを受け取ります。

   ```java
   MediaResource mediaResource =  
     MediaResource.createFromUrl("www.example.com/video/test_video.m3u8", 
                                 timeRanges.toMetadata(metadata));
   ```
