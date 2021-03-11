---
description: 新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。 MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。
title: メディアリソースの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# メディアリソースの作成{#create-a-media-resource}

新しいビデオコンテンツごとに、ビデオコンテンツに関する情報でMediaResourceインスタンスを初期化し、メディアリソースを読み込みます。 MediaResourceクラスは、MediaPlayerインスタンスによって読み込まれるコンテンツを表します。

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
    <td colname="col2"> <p>指定されたファイルの種類に対応する<span class="codeph"> MediaResource.Type </span>定義済みリストの次のいずれかのメンバーです。 
    <ul id="ul_72636C41CA7E4538A3BE11A79E0282FC"> 
    <li id="li_070960200DEB40E992C58FCB8909AEA3"> <span class="codeph"> HLS  </span> - M3U8 </li> 
    </ul> </p> </td> 
    </tr> 
    <tr> 
    <td colname="col1"> <p>metadata </p> </td> 
    <td colname="col2"> <p><span class="codeph"> Metadata </span>クラスのインスタンス。読み込むコンテンツに関するカスタム情報を含む場合があります。 </p> <p>コンテンツの例としては、メインコンテンツ内に配置する代替コンテンツや広告コンテンツがあります。 広告を使用する場合は、<span class="codeph"> AuditudeSettings </span>を設定します。 詳しくは、<a href="../../../tvsdk-1.4-for-android/ad-insertion/ad-insertion-metadata/android-1.4-ad-insertion-metadata-set-up.md" format="dita" scope="local">Ad Insertionメタデータ</a>を参照してください。 </p> </td> 
    </tr> 
    </tbody> 
    </table>

   >[!IMPORTANT]
   >
   >TVSDKは、特定のタイプのコンテンツの再生のみをサポートします。 その他のタイプのコンテンツを読み込もうとすると、TVSDKはエラーイベントをディスパッチします。
   >
   >MP4ビデオオンデマンド(VOD)コンテンツの場合、TVSDKは、トリック再生、可変ビットレート(ABR)ストリーミング、広告挿入、クローズドキャプションまたはDRMをサポートしません。

   次のコードは、`MediaResource`インスタンスを作成します。

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
   >この時点で、`MediaResource`アクセサ(getter)を使用して、リソースの種類、URL、およびメタデータを調べることができます。

1. 次を使用して、メディアリソースを読み込みます。

   * MediaPlayerインスタンス。

      詳しくは、[MediaPlayerへのメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-resource-load.md)を参照してください。
   * `MediaPlayerItemLoader`詳しくは、[MediaPlayerItemLoaderを使用したメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md)を参照してください。
   >[!IMPORTANT]
   >
   >メディアリソースをバックグラウンドスレッドに読み込まないでください。 ほとんどのTVSDK操作は、メインスレッドで実行する必要があり、バックグラウンドスレッドで実行すると、操作がエラーをスローして終了する可能性があります。
