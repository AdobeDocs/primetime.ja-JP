---
description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 TVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
seo-description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 TVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
seo-title: ID3タグ
title: ID3タグ
uuid: 5e5c5f89-7653-47c1-b9c1-6b9b9b1f8d73
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ID3タグ {#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 TVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDKは、可能なエンコーディング（ASCII、UTF8、UTF16-BEまたはUTF16-LE）のいずれかで、オーディオ(AAC)ストリームおよびビデオ(H.264)ストリームのID3メタデータ（バージョン2.3.0または2.4.0）を認識します。 認識されるバージョンまたは形式に含まれないID3タグは無視されます。 未指定のエンコーディングはUTF8として扱われます。

TVSDKは、ID3メタデータを検出すると、次のデータを含む通知を発行します。

* InfoCode = 303007
* TYPE = ID3
* NAME =存在しない
* ID = 0

1. のイベントリスナーを実装し `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` 、オブジェクトに登録 `MediaPlayer` します。

   TVSDKは、ID3メタデータを検出すると、このリスナーを呼び出します。

   >[!NOTE]
   >
   >カスタム広告キューは、同じイベントを `onTimedMetadata` 使用して新しいタグの検出を示します。 カスタム広告キューがマニフェストレベルで検出され、ID3タグがストリームに埋め込まれるので、混乱の原因になりません。 詳しくは、custom-tags-configureを参照してください。

1. メタデータを取得します。

   ```java
   @Override 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```

