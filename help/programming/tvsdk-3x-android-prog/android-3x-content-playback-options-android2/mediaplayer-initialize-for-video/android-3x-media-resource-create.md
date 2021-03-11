---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# メディアリソースの作成{#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関する情報を`MediaResource`コンストラクタに渡して、`MediaResource`を作成します。

   `MediaResource`コンストラクターには次のパラメーターが必要です。

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> コンストラクタパラメータ </th> 
      <th colname="col2" class="entry"> 説明 </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> <span class="codeph"> url  </span> </td> 
      <td colname="col2"> メディアのマニフェスト/プレイリストのURLを表す文字列。 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> type  </span> </td> 
      <td colname="col2"> <span class="codeph"> MediaResource.Type </span> enumの次のメンバーの1つで、指定されたファイルの種類に対応します。 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS  </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF  </span> - ISOベースのメディアファイル形式(MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH  </span> - MPEG-DASHメディアプレゼンテーション説明(MPD) </li> 
      </ul> </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> metadata  </span> </td> 
      <td colname="col2"> <span class="codeph"> Metadata </span>クラスのインスタンス（辞書に似た構造体）。メインコンテンツ内に配置する代替コンテンツや広告コンテンツなど、読み込まれるコンテンツに関する追加情報を含む場合があります。 広告を使用する場合は、このコンストラクタ<a href="/help/programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-insertion-metadata/android-3x-ad-insertion-metadata.md">広告挿入メタデータ</a>を使用する前に、<span class="codeph"> AuditudeSettings </span>を設定します。 </td> 
   </tr> 
   </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、TVSDKはエラーイベントをディスパッチします。
   >
   >MP4ビデオオンデマンド(VOD)コンテンツの場合、TVSDKは、トリック再生、可変ビットレート(ABR)ストリーミング、広告挿入、クローズドキャプションまたはDRMをサポートしません。

   次のコードは、`MediaResource`インスタンスを作成します。        >

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
   MediaResource.Type.HLS, 
     metadata); 
   ```

   この手順の後いつでも、`MediaResource`アクセサ(getter)を使用して、リソースの種類、URL、およびメタデータを調べることができます。

1. 次のいずれかのオプションを使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。
   * `MediaPlayerItemLoader` 詳しくは、MediaPlayerItemLoaderを使用したメディアリソースの [読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)。

   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどのTVSDK操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がエラーをスローして終了する可能性があります。
