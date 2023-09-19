---
description: MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、 MediaResource インスタンスをビデオコンテンツに関する情報で初期化し、メディアリソースを読み込みます。

MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

1. の作成 `MediaResource` メディアに関する情報を `MediaResource` コンストラクタ。

   The `MediaResource` コンストラクターには次のパラメーターが必要です。

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
      <td colname="col2"> メディアのマニフェスト/プレイリストの URL を表す文字列。 </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> type </span> </td>
      <td colname="col2"> 次に掲げる <span class="codeph"> MediaResource.Type </span> 指定されたファイルタイプに対応する列挙型。
      <ul id="ul_C286ED3C31364B858A1C9AF3356E9282">
      <li id="li_25B24EF76D8849DE8764539F25E435FA"> <span class="codeph"> HLS </span> - M3U8 </li>
      <li id="li_1344A41B434D49229E392F1AAF9ECA81"> <span class="codeph"> ISOBMFF </span> - ISO ベースのメディアファイル形式 (MP4) </li>
      <li id="li_92392073B7334916B06B16570C51AC91"> <span class="codeph"> DASH </span> - MPEG-DASH メディアプレゼンテーションの説明 (MPD) </li>
      </ul> </td>
      </tr>
      <tr>
      <td colname="col1"> <span class="codeph"> メタデータ </span> </td>
      <td colname="col2"> のインスタンス <span class="codeph"> メタデータ </span> クラス（辞書に似た構造体）。読み込まれるコンテンツに関する追加情報（メインコンテンツ内に配置する代替コンテンツや広告コンテンツなど）が含まれている場合があります。 広告を使用している場合は、 <span class="codeph"> AuditudeSettings </span> このコンストラクタを使用する前に、 </td>
      </tr>
      </tbody>
   </table>

   >[!IMPORTANT]
   >
   >TVSDK は、特定のタイプのコンテンツの再生のみをサポートしています。 その他のタイプのコンテンツの読み込みを試みると、 TVSDK はエラーイベントをディスパッチします。
   >
   >MP4 ビデオオンデマンド (VOD) コンテンツの場合、 TVSDK は、トリック再生、アダプティブビットレート (ABR) ストリーミング、広告挿入、クローズドキャプションまたは DRM をサポートしません。

   次のコードは、 `MediaResource` インスタンス：

   ```java
   // To do: Create metadata here
   MediaResource res = new MediaResource(
     "https://www.example.com/video/some-video.m3u8",
     MediaResource.Type.HLS,
     metadata);
   ```

   この手順の後は、いつでも `MediaResource` リソースのタイプ、URL、メタデータを調べるアクセサ (getter)。

1. 次のいずれかのオプションを使用して、メディアリソースを読み込みます。

   * MediaPlayer インスタンス。
   * `MediaPlayerItemLoader` 詳しくは、 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-2.7-for-android/content-playback-options/mediaplayer-initialize-for-video/t-psdk-android-2.7-media-resource-load-using-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどの TVSDK 操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がスローされて終了する場合があります。
