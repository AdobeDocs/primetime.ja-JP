---
description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-description: MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-title: メディアリソースの作成
title: メディアリソースの作成
uuid: c25c037e-e9a0-430c-a150-b75a9ac051b1
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# メディアリソースの作成{#create-a-media-resource}

MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

1. メディアに関する情報を`MediaResource`コンストラクタに渡して、`MediaResource`を作成します。

   <table id="table_DD0D5D9129D54F73881399B9B4FF546A"> 
    <thead> 
    <tr> 
    <th colname="col1" class="entry"> コンストラクタパラメータ </th> 
    <th colname="col2" class="entry"> 説明 </th> 
    </tr> 
    </thead>
    <tbody> 
    <tr> 
    <td colname="col1"> <p>url </p> </td> 
    <td colname="col2"> <p>メディアのマニフェスト/プレイリストのURLを表す文字列です。 </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>type </p> </td> 
    <td colname="col2"> <p>指定されたファイルの種類に対応する<span class="codeph"> MediaResource.Type </span>定義済みリストの次のいずれかのメンバーです。 </p> <p> 
    <ul id="ul_E9689FA06DC94BF4848F16E1F2F01A59"> 
    <li id="li_83A14B96CDC648C6AF6F5FA745343E1F"> <span class="codeph"> MP4  </span> - ISOベースのメディアファイル形式(MP4) </li> 
    <li id="li_FCD355151515412D9A78C3815DD09129"> <span class="codeph"> HLS  </span> - M3U8 </li> 
    <li id="li_9D3D306D49264830AC6EFB1F49524A3B"> <span class="codeph"> DASH  </span> - MPD </li> 
    </ul> </p> <p></p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p><span class="codeph"> Metadata </span>クラスのインスタンス。読み込むコンテンツに関するカスタム情報を含む場合があります。 コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 advertisingを使用する場合は、このコンストラクタを使用する前に、<span class="codeph"> AuditudeSettings </span>を設定してください。 詳しくは、<a href="../../ad-insertion/ad-insertion-metadata/c-psdk-browser-tvsdk-2.4-ad-insertion-metadata.md">Ad-insertion-metadata</a>を参照してください。 </p> <p>ヒント： 必要に応じて、メディアリソースの作成時に<span class="codeph"> forceFlash </span>パラメーターを使用して、Flashのフォールバックを強制できます。 これは、現在、Browser TVSDKでサポートされていない機能(ライブ広告ワークフローなど)があるので、役に立ちます。 Flashのフォールバックは、ビデオコンテンツの再生に使用されます。 </p> </td> 
    </tr> 
    </tbody> 
   </table>

   >[!IMPORTANT]
   >
   >ブラウザーTVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、Browser TVSDKはエラーイベントをディスパッチします。

   次のコードは、`MediaResource`インスタンスを作成します。

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
   >この後いつでも、`MediaResource`アクセサ(getter)を使って、リソースの種類、URL、およびメタデータを調べることができます。

1. MediaPlayerインスタンスを読み込みます。 詳しくは、[MediaPlayerへのメディアリソースの読み込み](../../content-playback-options-browser-tvsdk/mediaplayer-initialize-for-video/t-psdk-browser-tvsdk-2.4-media-resource-load.md)を参照してください。
