---
description: TVSDK には、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに関する固有の要件があります。
title: 要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 要件 {#requirements}

TVSDK には、メディアコンテンツ、マニフェストコンテンツ、DRM、ソフトウェアバージョンに固有のプロパティが必要です。

## システムおよびソフトウェアの要件 {#section_96E5B079900246E78682AE44D3F23068}

TVSDK を使用するには、ハードウェア、オペレーティングシステム、アプリケーションのバージョンがすべて、以下に示す最小要件を満たしていることを確認します。

| オペレーティングシステム | iOS 7.0 以降 |
|---|---|
| Xcode | iOS 12 の Xcode 10 とiOS 11 の Xcode 9 |

## コンテンツとマニフェストの要件 {#section_72DD0E4DA9774DCCADB42887497F1386}

DRM 暗号化キーを含む、ストリームと再生リスト（マニフェスト）の制限事項と要件を確認します。

| コンテンツセグメントのキーフレーム | 各コンテンツセグメントは、キーフレームで始まる必要があります。 |
|---|---|
| ライブ/リニアビデオのシーケンス番号 | 特定の時点で、メインコンテンツのすべてのビットレートレンディション間で一致する必要があります。 |

## EXT-X-VERSION の要件 {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

[!DNL .m3u8] マニフェストファイル内の `#EXT-X-VERSION` のバージョンは、アプリケーションで使用可能な機能と、有効なタグの `EXT` に影響します。

HLS プロトコルのバージョンを指定する `#EXT-X-VERSION` タグに関する情報を以下に示します。

* バージョンは、HLS プレイリストの機能と属性に一致する必要があります。一致しない場合は、再生エラーが発生する可能性があります。詳しくは、[HTTP ライブストリーミングの仕様 ](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) を参照してください。
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
   <td colname="2"> <span class="codeph"> EXT-X-KEY </span> タグの IV 属性。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF </span> 期間値 <p>バージョン 2 の duration タグ (<span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) は、整数値に丸められました。バージョン 3 以降では、浮動小数点での期間を正確に指定する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4 </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_5E73D41AF6DC4CEE88D6C029FFCFC350"><span class="codeph"> EXT-X-BYTERANGE </span> タグ </li> 
     <li id="li_BF5141F516F749E5890860D487EB5287"><span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> タグ </li> 
     <li id="li_E0D399A13812499B94107CDE62998EE9">The <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> タグ </li> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B">The <span class="codeph"> EXT-X-MEDIA </span> タグ </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD">The <span class="codeph"> オーディオ </span> および <span class="codeph"> ビデオ </span> の属性 <span class="codeph"> EXT-X-STREAM-INF </span> タグ </li> 
     <li id="li_DB2A7847D5884F6E91FD9E78101FBCA5">TVSDK 代替オーディオ </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
