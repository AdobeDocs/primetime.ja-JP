---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-title: メディアリソースの作成
title: メディアリソースの作成
uuid: c25c037e-e9a0-430c-a150-b75a9ac051b1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# メディアリソースの作成 {#create-a-media-resource}

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関す `MediaResource` る情報をコンストラクターに渡して、を作成 `MediaResource` します。

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> コンストラクターパラメーター </th> 
    <th colname="col2" class="entry"> 説明 </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>メディアのマニフェスト/プレイリストのURLを表す文字列。 </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>指定されたファイルの種類に対応する、MediaResource.Type <span class="codeph"> 列挙 </span> の次のいずれかのメンバーです。 </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - ISOベースのメディアファイル形式(MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>メタデータ </p> </td> 
    <td colname="col2"> <p>読み込むコンテンツに関す <span class="codeph"> るカ </span> スタム情報を含む可能性のあるMetadataクラスのインスタンス。 コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用する場合は、このコンストラクターを使 <span class="codeph"> 用する前 </span> にAuditudeSettingsを設定してください。 詳しくは、 <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-insertion-metadataを参照してください</a>。 </p> <p>ヒント： 必要に応じて、メディアリソースの作成時にforceFlashパラメータを使用して、Flash <span class="codeph"> のフォー </span> ルバックを強制することができます。 現在、すべての機能（ライブ広告ワークフローなど）がブラウザーTVSDKでサポートされているわけではないので、この方法が役に立ちます。 Flashフォールバックは、ビデオコンテンツの再生に使用されます。 </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >ブラウザーTVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、ブラウザーTVSDKはエラーイベントをディスパッチします。

   次のコードでは、インスタンスを作成 `MediaResource` します。

   ```js
   //create a MediaResource instance pointing to some HLS content 
   Metadata metadata = //TODO: create metadata here 
   mediaResource = new AdobePSDK.MediaResource ( 
         "https://www.example.com/video/some-video.m3u8", 
         AdobePSDK.MediaResourceType.HLS,  
         metadata);
   ```

   >[!TIP]
   >
   >この後は、アクセサ(getter)を使用して、リ `MediaResource` ソースのタイプ、URL、およびメタデータをいつでも確認できます。

1. MediaPlayerインスタンスを読み込みます。 詳しくは、MediaPlayerでのメディアリ [ソースの読み込みを参照してください](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md)。
