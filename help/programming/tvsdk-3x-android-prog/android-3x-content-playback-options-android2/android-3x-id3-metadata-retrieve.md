---
description: ID3 タグは、ファイルのタイトルやアーティスト名など、オーディオまたはビデオファイルに関する情報を提供します。 TVSDK は、HLS ストリームのトランスポートストリーム (TS) セグメントレベルで ID3 タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
title: ID3 タグ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# ID3 タグ {#id-tags}

ID3 タグは、ファイルのタイトルやアーティスト名など、オーディオまたはビデオファイルに関する情報を提供します。 TVSDK は、HLS ストリームのトランスポートストリーム (TS) セグメントレベルで ID3 タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDK は、可能なエンコーディング (ASCII、UTF8、UTF16-BE、UTF16-LE) で、オーディオ (AAC) およびビデオ (H.264) ストリームの ID3 メタデータ（バージョン 2.3.0 または 2.4.0）を認識します。 認識されるバージョンまたは形式のいずれにも含まれない ID3 タグは無視されます。 未指定のエンコードは UTF8 として扱われます。

TVSDK は、ID3 メタデータを検出すると、次のデータを含む通知を発行します。

* TYPE = ID3
* 名前= ID3

1. のイベントリスナーを実装します。 `MediaPlayer.TimedMetadataEventListener#onTimedMetadata(TimeMetadata timeMetadata)` そして次に登録します。 `MediaPlayer` オブジェクト。

   TVSDK は、このリスナーを検出したときにこのリスナーを呼び出します。 `ID3` メタデータ。

   >[!TIP]
   >
   >カスタム広告キューは同じを使用します `onTimedMetadata` イベントを使用して、新しいタグの検出を示します。 カスタム広告キューはマニフェストレベルで検出され、ID3 タグがストリームに埋め込まれるので、これによって混乱が生じることはありません。 詳しくは、 [カスタムタグ](../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/custom-tags-configure/android-3x-custom-tags-configure.md).

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
               byte[] value = metadata.getByteArray(key); 
           } 
       } 
   }
   ```
