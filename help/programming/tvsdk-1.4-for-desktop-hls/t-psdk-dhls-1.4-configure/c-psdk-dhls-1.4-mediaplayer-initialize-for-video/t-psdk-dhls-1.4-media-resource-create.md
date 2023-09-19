---
description: MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、 MediaResource インスタンスをビデオコンテンツに関する情報で初期化し、メディアリソースを読み込みます。

MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

1. の作成 `MediaResource` メディアに関する情報を `MediaResource` コンストラクタ。

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> コンストラクターパラメーター </th> 
      <th colname="col2" class="entry"> 説明 </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>メディアのマニフェスト/プレイリストの URL を表す string。 </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>指定されたファイルタイプに対応する、次の string 値のいずれかです。 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span> - ISO ベースのメディアファイル形式 (MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> メタデータ</span> </td> 
      <td colname="col2"> <p>のインスタンス <span class="codeph"> メタデータ</span> クラス。読み込むコンテンツに関するカスタム情報を含む場合があります。 </p> <p>コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用している場合は、 <span class="codeph"> AuditudeSettings</span> このコンストラクタを使用する前に、 詳しくは、 <a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local"> Ad Insertionメタデータ</a>. </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDK は、特定のタイプのコンテンツの再生のみをサポートしています。 その他のタイプのコンテンツの読み込みを試みると、 TVSDK はエラーイベントをディスパッチします。
   >
   >MP4 ビデオオンデマンド (VOD) コンテンツの場合、 TVSDK は、トリック再生、アダプティブビットレート (ABR) ストリーミング、広告挿入、クローズドキャプションまたは DRM をサポートしません。

   次のコードは、 `MediaResource` インスタンス：

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >この時点で、 `MediaResource` リソースのタイプ、URL、メタデータを調べるアクセサ (getter)。

1. 次のいずれかを使用して、メディアリソースを読み込みます。

   * お使いの MediaPlayer インスタンス。

     詳しくは、 [Mediaplayer でのメディアリソースの読み込み](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` 詳しくは、 [Mediaplayer でのメディアリソースの読み込み](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md).
