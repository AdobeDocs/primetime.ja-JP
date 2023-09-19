---
description: 新しいビデオコンテンツごとに、 MediaResource インスタンスをビデオコンテンツに関する情報で初期化し、メディアリソースを読み込みます。 MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# メディアリソースの作成 {#create-a-media-resource}

新しいビデオコンテンツごとに、 MediaResource インスタンスをビデオコンテンツに関する情報で初期化し、メディアリソースを読み込みます。 MediaResource クラスは、 MediaPlayer インスタンスによって読み込まれるコンテンツを表します。

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
    <td colname="col2"> <p>次に掲げる <span class="codeph"> MediaResource.Type </span> 指定されたファイルタイプに対応する列挙： 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>メタデータ </p> </td> 
    <td colname="col2"> <p>のインスタンス <span class="codeph"> メタデータ </span> クラス。読み込むコンテンツに関するカスタム情報を含む場合があります。 </p> <p>コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用している場合は、 <span class="codeph"> AuditudeSettings </span>. 詳しくは、 <a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local"> Ad Insertionメタデータ </a>. </p> </td> 
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
   >この時点で、 `MediaResource` リソースのタイプ、URL、メタデータを調べるアクセサ (getter)。

1. 次を使用して、メディアリソースを読み込みます。

   * お使いの MediaPlayer インスタンス。

     詳しくは、 [MediaPlayer でのメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md).
   * A `MediaPlayerItemLoader` 詳しくは、 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどの TVSDK 操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がスローされて終了する場合があります。
