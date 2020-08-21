---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-title: メディアリソースの作成
title: メディアリソースの作成
uuid: 9ae86c04-7bbe-43fb-9f57-1d9fa2fa73d0
translation-type: tm+mt
source-git-commit: bdeab54aeb083f1fc8d27db1fd94bf89d74429da
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関する情報 `MediaResource` をコンストラクタに渡して、を作成し `MediaResource` ます。

   コンストラクターには、次のパラメーターが必要です。 `MediaResource`

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
   <thead> 
   <tr> 
      <th colname="col1" class="entry"> コンストラクタパラメータ </th> 
      <th colname="col2" class="entry"> 説明 </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col1"> <span class="codeph"> url </span> </td> 
      <td colname="col2"> メディアのマニフェスト/プレイリストのURLを表す文字列。 </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> type </span> </td> 
      <td colname="col2"> 指定されたファイルの種類に対応する、MediaResource.Type <span class="codeph"></span> enumの次のメンバの1つ： 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISOベースのメディアファイル形式(MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - MPEG-DASHメディアプレゼンテーション説明(MPD) </li> 
      </ul> </td> 
   </tr> 
   <tr> 
      <td colname="col1"> <span class="codeph"> metadata </span> </td> 
      <td colname="col2"> Metadata <span class="codeph"></span> クラスのインスタンス（ディクショナリに似た構造体）。メインコンテンツ内に配置する代替コンテンツや広告コンテンツなど、読み込まれるコンテンツに関する追加情報を含む場合があります。 広告を使用する場合、このコンストラクターの <span class="codeph"> Ad insertionメタデータを使用する前に、AuditudeSettingsを設定 </span><a href="/help/programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-insertion-metadata/android-3x-ad-insertion-metadata.md"></a>します。 </td> 
   </tr> 
   </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、TVSDKはエラーイベントをディスパッチします。
   >
   >MP4ビデオオンデマンド(VOD)コンテンツの場合、TVSDKは、トリック再生、可変ビットレート(ABR)ストリーミング、広告挿入、クローズドキャプションまたはDRMをサポートしません。

   次のコードは、インスタンスを作成し `MediaResource` ます。       >

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
   MediaResource.Type.HLS, 
     metadata); 
   ```

   この手順の後はいつでも、アク `MediaResource` セサ(getter)を使用して、リソースの種類、URL、およびメタデータを調べることができます。

1. 次のいずれかのオプションを使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。
   * `MediaPlayerItemLoader` 詳しくは、MediaPlayerItemLoaderを使用したメディアリソースの [読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)。

   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどのTVSDK操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がエラーをスローして終了する可能性があります。
