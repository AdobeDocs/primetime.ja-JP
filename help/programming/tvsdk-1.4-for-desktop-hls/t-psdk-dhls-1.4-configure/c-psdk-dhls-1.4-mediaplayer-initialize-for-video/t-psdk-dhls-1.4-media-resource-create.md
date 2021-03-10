---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# メディアリソースの作成{#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関する情報を`MediaResource`コンストラクタに渡して、`MediaResource`を作成します。

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
      <tr> 
      <th colname="col1" class="entry"> コンストラクタパラメータ </th> 
      <th colname="col2" class="entry"> 説明 </th> 
      </tr>
    </thead>
    =<tbody> 
      <tr> 
      <td colname="col1"><span class="codeph"> url</span> </td> 
      <td colname="col2"> <p>メディアのマニフェスト/プレイリストのURLを表す文字列です。 </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> type</span> </td> 
      <td colname="col2"> <p>指定されたファイルタイプに対応する次のstring値のいずれかです。 
        <ul id="ul_7512E90B7B294EF9BFBA2D68DE678CBB"> 
        <li id="li_AA84434E84184A3D909552794B425ABD"><span class="codeph"> MP4</span>  - ISOベースのメディアファイル形式(MP4) </li> 
        <li id="li_8A2F3752569344B59EE30303A8393488"><span class="codeph"> HLS</span> - M3U8 </li> 
        </ul> </p> </td> 
      </tr> 
      <tr> 
      <td colname="col1"><span class="codeph"> metadata</span> </td> 
      <td colname="col2"> <p><span class="codeph"> Metadata</span>クラスのインスタンス。読み込むコンテンツに関するカスタム情報を含む場合があります。 </p> <p>コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用する場合は、このコンストラクタを使用する前に、<span class="codeph"> AuditudeSettings</span>を設定してください。 詳しくは、<a href="../../../tvsdk-1.4-for-desktop-hls/ad-insertion/ad-insertion-metadata/c-psdk-dhls-1.4-ad-insertion-metadata.md" format="dita" scope="local">Ad Insertionメタデータ</a>を参照してください。 </p> </td> 
      </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >TVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、TVSDKはエラーイベントをディスパッチします。
   >
   >MP4ビデオオンデマンド(VOD)コンテンツの場合、TVSDKは、トリック再生、可変ビットレート(ABR)ストリーミング、広告挿入、クローズドキャプションまたはDRMをサポートしません。

   次のコードは、`MediaResource`インスタンスを作成します。

   ```
   // To do: Create metadata here
   MyResource = new MediaResource(
            "https://www.example.com/video/some-video.m3u8", 
            "HLS",
            MyMetadata)
   ```

   >[!TIP]
   >
   >この時点で、`MediaResource`アクセサ(getter)を使用して、リソースの種類、URL、およびメタデータを調べることができます。

1. 次のいずれかを使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。

      詳しくは、[Mediaplayerでのメディアリソースの読み込み](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md)を参照してください。
   * `MediaPlayerItemLoader`詳しくは、[Mediaplayer](../../../tvsdk-1.4-for-desktop-hls/t-psdk-dhls-1.4-configure/c-psdk-dhls-1.4-mediaplayer-initialize-for-video/t-psdk-dhls-1.4-media-resource-load.md)でのメディアリソースの読み込みを参照してください。

