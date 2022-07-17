---
description: TVSDK には、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに関する固有の要件があります。
title: 要件
exl-id: 85bf7b85-5f4b-4ed5-aa4f-765dabc5d4d8
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# 要件 {#requirements}

TVSDK には、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに関する固有の要件があります。

## システムおよびソフトウェアの要件 {#section_96E5B079900246E78682AE44D3F23068}

TVSDK を使用するには、ハードウェア、オペレーティングシステム、アプリケーションのバージョンがすべて、以下に示す最小要件を満たしていることを確認します。

| オペレーティングシステム | Android 4.0 以降（API レベル 14 以降） |
|---|---|
| CPU | 1 GHz シングルコアまたは同等 |
| RAM | 256 MB |
| GPU | 再生に必要なハードウェア GPU |
| アーキテクチャ | Houdini、ARM64、ARMv7、ARMv8 を介した x86 |

## コンテンツとマニフェストの要件 {#section_72DD0E4DA9774DCCADB42887497F1386}

DRM 暗号化キーを含む、ストリームと再生リスト（マニフェスト）の制限事項と要件を確認します。

| Adobeアクセス DRM | DRM 保護されたストリームがマルチビットレート (MBR) の場合、MBR に使用される DRM 暗号化キーは、すべてのビットレートストリームで使用されるキーと同じである必要があります。 |
|---|---|
| 広告バリアントマニフェスト | メインコンテンツのレンディションと同じビットレートレンディションが必要です。 |

## #EXT-X-VERSIONの要件 {#section_49A33664651A46EC9ED888BA9C1C3F6D}

のバージョン。 `#EXT-X-VERSION` 内 [!DNL .m3u8] マニフェストファイルは、アプリケーションで使用可能な機能と対象となる機能に影響します `EXT` タグは有効です。

以下に、 `#EXT-X-VERSION` タグ。HLS プロトコルのバージョンを指定します。

* バージョンは、HLS プレイリスト内の機能と属性に一致する必要があります。そうしないと、再生エラーが発生する場合があります。 詳しくは、 [HTTP ライブストリーミング仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1).
* Adobeでは、 TVSDK ベースのクライアントでの再生に、少なくともバージョン 2 の HLS を使用することをお勧めします。

   クライアントおよびサーバーは、次の方法でバージョンを実装する必要があります。

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 少なくともこのバージョンを使用する </th> 
   <th colname="2" class="entry"> 次の機能を使用するには </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> の IV 属性 <span class="codeph"> EXT-X-KEY </span> タグを使用します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF </span> 期間の値 <p>The duration tags ( <span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) in version 2 were rounded to integer values. バージョン 3 以降では、浮動小数点での期間を正確に指定する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350">この <span class="codeph"> EXT-X-BYTERANGE </span> タグ </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287">この <span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> タグ </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">この <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> タグ </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">この <span class="codeph"> EXT-X-MEDIA </span> タグ </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">この <span class="codeph"> オーディオ </span> および <span class="codeph"> ビデオ </span> の属性 <span class="codeph"> EXT-X-STREAM-INF </span> タグ </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">TVSDK 代替オーディオ </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
