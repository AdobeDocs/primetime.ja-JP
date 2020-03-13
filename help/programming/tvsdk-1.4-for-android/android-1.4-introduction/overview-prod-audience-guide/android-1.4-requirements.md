---
description: TVSDKは、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに固有の要件を必要とします。
seo-description: TVSDKは、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに固有の要件を必要とします。
seo-title: 要件
title: 要件
uuid: d5671444-cc83-48d4-8ce6-735d5f373795
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 要件 {#requirements}

TVSDKは、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに固有の要件を必要とします。

## システムとソフトウェアの要件 {#section_96E5B079900246E78682AE44D3F23068}

TVSDKを使用するには、お使いのハードウェア、オペレーティングシステム、アプリケーションのバージョンがすべて、以下に示す最小要件を満たしていることを確認します。

| オペレーティングシステム | Android 4.0以降（APIレベル14以上） |
|---|---|
| CPU | 1 GHzシングルコアまたは同等 |
| RAM | 256 MB |
| GPU | 再生に必要なハードウェアGPU |
| アーキテクチャ | x86（Houdini、ARM64、ARMv7、ARMv8経由） |

## コンテンツとマニフェストの要件 {#section_72DD0E4DA9774DCCADB42887497F1386}

DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限と要件を確認します。

| Adobe Access DRM | DRM保護されたストリームがマルチビットレート(MBR)の場合、MBRに使用されるDRM暗号化キーは、すべてのビットレートストリームで使用されるキーと同じである必要があります。 |
|---|---|
| 広告バリアントマニフェスト | メインコンテンツのレンディションと同じビットレートレンディションが必要です。 |

## #EXT-X-VERSIONの要件 {#section_49A33664651A46EC9ED888BA9C1C3F6D}

ファイル内ののバ `#EXT-X-VERSION` ージョ [!DNL .m3u8] ンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで `EXT` 有効なタグに影響を与えます。

HLSプロトコルのバージョンを指定する `#EXT-X-VERSION` タグに関する情報を次に示します。

* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。 詳しくは、 [HTTPライブストリーミングの仕様を参照してください](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)。
* TVSDKベースのクライアントでの再生には、少なくともバージョン2のHLSを使用することをお勧めします。

   クライアントおよびサーバーは、次の方法でバージョンを実装する必要があります。

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 少なくともこのバージョンを使用する </th> 
   <th colname="2" class="entry"> これらの機能を使用するには </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> EXT-X-KEYタ <span class="codeph"> グのIV属性 </span> 。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF期 </span> 間値 <p>期間タグ( <span class="codeph"> #EXTINF:バー </span>ジョン2の&lt;duration&gt;,&lt;title&gt;)は、整数値に丸められました。 バージョン3以降では、浮動小数点で正確に指定する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">EXT- <span class="codeph"> X-BYTERANGEタ </span> グ </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">EXT-X-I-FRAME-STREAM-INFタ <span class="codeph"></span> グ </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">EXT- <span class="codeph"> X-I-FRAMES-ONLYタ </span> グ </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">EXT- <span class="codeph"> X-MEDIAタ </span> グ </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD"><span class="codeph"> EXT-X-STREAM-INF </span> タ <span class="codeph"> グのAUDIO属性とVIDEO属 </span><span class="codeph"></span> 性 </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">TVSDK代替オーディオ </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

