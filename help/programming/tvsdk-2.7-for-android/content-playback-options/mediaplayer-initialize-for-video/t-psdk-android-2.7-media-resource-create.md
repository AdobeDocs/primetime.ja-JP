---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-title: メディアリソースの作成
title: メディアリソースの作成
uuid: f34a11a3-dac2-405e-8632-1d9617cc019d
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関す `MediaResource` る情報をコンストラクターに渡して、を作成 `MediaResource` します。

   コンストラ `MediaResource` クターには次のパラメーターが必要です。

   <table id="table_22886D6770FB45E99D35D0B90E6CC302"> 
      <thead> 
      <tr> 
      <th colname="col1" class="entry"> コンストラクターパラメーター </th> 
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
      <td colname="col2"> 指定されたファイルの種類に対応する、 <span class="codeph"> MediaResource.Type </span> enumの次のいずれかのメンバーです。 
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282"> 
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li> 
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISOベースのメディアファイル形式(MP4) </li> 
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - MPEG-DASHメディアプレゼンテーション説明(MPD) </li> 
      </ul> </td> 
      </tr> 
      <tr> 
      <td colname="col1"> <span class="codeph"> メタデータ </span> </td> 
      <td colname="col2"> メインコンテンツ内に配置する代替コンテンツや広告コンテンツなど、読み込まれるコンテンツに関する追加情報を含む <span class="codeph"> Metadata </span> クラスのインスタンス（ディクショナリに似た構造）。 広告を使用する場合は、このコンストラク <span class="codeph"> ターを使 </span> 用する前にAuditudeSettingsを設定します(を参照し <a keyref="ad-insertion-metadata"></a>てください)。 </td> 
      </tr> 
      </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、TVSDKはエラーイベントをディスパッチします。
   >
   >MP4ビデオオンデマンド(VOD)コンテンツの場合、TVSDKは、トリック再生、可変ビットレート(ABR)ストリーミング、広告挿入、クローズドキャプションまたはDRMをサポートしません。

   次のコードでは、インスタンスを作成 `MediaResource` します。

   ```java
   // To do: Create metadata here 
   MediaResource res = new MediaResource( 
     "https://www.example.com/video/some-video.m3u8",  
     MediaResource.Type.HLS, 
     metadata); 
   ```

   この手順の後は、アクセサ(getter)を使用して、リ `MediaResource` ソースのタイプ、URL、およびメタデータをいつでも確認できます。

1. 次のいずれかのオプションを使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。
   * `MediaPlayerItemLoader` 詳しくは、MediaPlayerItemLoaderを使用したメデ [ィアリソースの読み込みを参照してください](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md)。
   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどのTVSDK操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がエラーをスローして終了する可能性があります。
