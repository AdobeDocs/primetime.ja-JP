---
description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。
seo-description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。
seo-title: ID3タグ
title: ID3タグ
uuid: 5c016260-5ced-480e-897a-11ffe7f34441
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---


# ID3タグ{#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDKは、可能なエンコーディング（ASCII、UTF8、UTF16-BEまたはUTF16-LE）のいずれかで、オーディオ(AAC)およびビデオ(H.264)ストリームのID3メタデータ（バージョン2.3.0または2.4.0）を認識します。 認識されるバージョンまたは形式に含まれないID3タグは無視されます。 未指定のエンコーディングはUTF8として扱われます。

TVSDKは、ID3メタデータを検出すると、次のデータを含む通知を発行します。

* InfoCode = 303007
* TYPE = ID3
* NAME =存在しません
* ID = 0

1. `TimedMetadataEvent.TIMED_METADATA_ID3_ADDED`のイベントリスナーを実装し、`MediaPlayer`オブジェクトに登録します。

   TVSDKは、ID3メタデータを検出すると、このリスナーを呼び出します。

   >[!NOTE]
   >
   >カスタム広告キューは、同じ`onTimedMetadata`イベントを使用して、新しいタグの検出を示します。 カスタム広告キューはマニフェストレベルで検出され、ID3タグはストリームに埋め込まれるので、混乱の原因になりません。 詳しくは、custom-tags-configureを参照してください。

1. メタデータを取得します。

   ```
   private function onID3Metadata(event:TimedMetadataEvent):void { 
       var timedMetadata:TimedMetadata = event.timedMetadata; 
       var metadata:Metadata = timedMetadata.metadata; 
       var keys:Vector.<String> = metadata.keySet(); 
       for (var i:int = keys.length - 1; i >= 0; --i) { 
           var value:ByteArray = metadata.getByteArray(keys[i]); 
           _logger.info("#onTimedMetadata Detected dictionary data key: [{0}],  
                        value: [{1}] of length {2} bytes at time [{3}].",  
                        keys[i],  
                        value.toString(),  
                        value.length,  
                        event.timedMetadata.time); 
       } 
   } 
   ```

