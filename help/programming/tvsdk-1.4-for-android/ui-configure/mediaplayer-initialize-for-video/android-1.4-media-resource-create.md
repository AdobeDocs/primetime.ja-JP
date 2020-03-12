---
description: 新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。 MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-description: 新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。 MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
seo-title: メディアリソースの作成
title: メディアリソースの作成
uuid: d9fe982a-bedf-445c-b5be-f7918693782a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。 MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

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
    <td colname="col2"> <p>指定されたファイルの種類に対応する、MediaResource.Type <span class="codeph"> 列挙 </span> の次のいずれかのメンバーです。 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>メタデータ </p> </td> 
    <td colname="col2"> <p>読み込むコンテンツに関す <span class="codeph"> るカ </span> スタム情報を含む可能性のあるMetadataクラスのインスタンス。 </p> <p>コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用する場合は、AuditudeSettingsを設定 <span class="codeph"> しま </span>す。 詳しくは、広告挿入メタデータを <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> 参照してくださ </a>い。 </p> </td> 
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
   try { 
       // create a MediaResource instance pointing to some HLS content 
       Metadata metadata = //TODO: create metadata  
       MediaResource mediaResource = MediaResource.createFromUrl( 
         "https://www.example.com/video/some-video.m3u8",  
         MediaResource.Type.HLS,  
         metadata); 
   } catch(IllegalArgumentException ex) { 
       // this exception is thrown if the URL does not point  
       // to a valid url. 
   } 
   ```

   >[!TIP]
   >
   >この時点で、アクセサ(getter)を使 `MediaResource` 用して、リソースのタイプ、URL、およびメタデータを調べることができます。

1. 次を使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。

      詳しくは、MediaPlayerでのメディアリ [ソースの読み込みを参照してください](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md)。
   * 詳しく `MediaPlayerItemLoader` は、MediaPlayerItemLoaderを使用したメデ [ィアリソースの読み込みを参照してください](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md)。
   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどのTVSDK操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がエラーをスローして終了する場合があります。
