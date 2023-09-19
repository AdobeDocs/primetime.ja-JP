---
description: MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# メディアリソースの作成 {#create-a-media-resource}

MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

1. の作成 `MediaResource` メディアに関する情報を `MediaResource` コンストラクタ。

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
    <td colname="col2"> <p>メディアのマニフェスト/プレイリストの URL を表す string。 </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>次に掲げる <span class="codeph"> MediaResource.Type </span> 指定されたファイルタイプに対応する列挙： </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4 </span> - ISO ベースのメディアファイル形式 (MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>メタデータ </p> </td> 
    <td colname="col2"> <p>のインスタンス <span class="codeph"> メタデータ </span> クラス。読み込むコンテンツに関するカスタム情報を含む場合があります。 コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用している場合は、 <span class="codeph"> AuditudeSettings </span> このコンストラクタを使用する前に、 詳しくは、 <a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-insertion-metadata</a>. </p> <p>ヒント：必要に応じて、 <span class="codeph"> forceFlash </span> パラメーターを使用して、メディアリソースを作成する場合に使用します。 現在、Browser TVSDK でサポートされていない機能（ライブ広告ワークフローなど）もあるので、この機能が役に立つ場合があります。 Flashフォールバックは、ビデオコンテンツの再生に使用されます。 </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >ブラウザー TVSDK は、特定のタイプのコンテンツの再生のみをサポートしています。 その他のタイプのコンテンツを読み込もうとすると、Browser TVSDK はエラーイベントをディスパッチします。

   次のコードは、 `MediaResource` インスタンス：

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
   >この後は、いつでも `MediaResource` リソースのタイプ、URL、メタデータを調べるアクセサ (getter)。

1. MediaPlayer インスタンスを読み込みます。 詳しくは、 [MediaPlayer でのメディアリソースの読み込み](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md).
