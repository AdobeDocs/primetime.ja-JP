---
description: TVSDK には、メディアコンテンツ、マニフェストコンテンツ、ソフトウェアバージョンに固有のプロパティが必要です。
title: 要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# 要件 {#requirements}

TVSDK には、メディアコンテンツ、マニフェストコンテンツ、ソフトウェアバージョンに固有のプロパティが必要です。

## システムおよびソフトウェアの要件 {#section_61C32A0209C44230B392B113B85643EE}

TVSDK を使用するには、ハードウェア、オペレーティングシステム、アプリケーションのバージョンがすべて、以下に示す最小要件を満たしていることを確認します。

オペレーティングシステム：iOS 6.0 以降

## コンテンツとマニフェストの要件 {#section_05FA02E2189742008DA09D87E66DCAB7}

DRM 暗号化キーを含む、ストリームと再生リスト（マニフェスト）の制限事項と要件を確認します。

| コンテンツセグメントのキーフレーム | 各コンテンツセグメントは、キーフレームで始まる必要があります。 |
|---|---|
| ライブ/リニアビデオのシーケンス番号 | 特定の時点で、メインコンテンツのすべてのビットレートレンディション間で一致する必要があります。 |

## #EXT-X-VERSIONの要件 {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

のバージョン。 `#EXT-X-VERSION` （内） [!DNL .m3u8] ファイルは、アプリケーションで使用可能な機能と、使用する機能に影響を与えます `EXT` タグは、プレイリスト/マニフェストで有効です。

HLS プロトコルのバージョンを指定する `#EXT-X-VERSION` タグに関する情報を以下に示します。

* バージョンは、HLS プレイリストの機能と属性に一致する必要があります。一致しない場合は、再生エラーが発生する可能性があります。

  詳しくは、[HTTP ライブストリーミングの仕様 ](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1) を参照してください。
* タグがマスターまたはメディア再生リストに含まれていない場合、またはバージョンが指定されていない場合は、デフォルトでバージョン 1 が使用されます。バージョン 1 に準拠していないコンテンツは再生されません。
* Adobeでは、TVSDK ベースのクライアントでの再生に少なくともバージョン 2 を使用することをお勧めします。

クライアントおよびサーバーは、次の方法でバージョンを実装する必要があります。

<table id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr> 
   <th colname="1" class="entry"> 少なくともこのバージョンを使用する </th> 
   <th colname="2" class="entry"> 次の機能を使用するには </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> の IV 属性 <span class="codeph"> EXT-X-KEY </span> タグを使用します。 </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF </span> 期間値 <p>バージョン 2 の duration タグ (<span class="codeph"> #EXTINF: </span>&lt;duration&gt;,&lt;title&gt;) は、整数値に丸められました。バージョン 3 以降では、浮動小数点値での期間が必要です。 </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> 広告挿入やシームレス ABR などの TVSDK 機能 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927"><span class="codeph"> EXT-X-BYTERANGE </span> タグ </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF"><span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span> タグ </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">The <span class="codeph"> EXT-X-I-FRAMES-ONLY </span> タグ </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">The <span class="codeph"> EXT-X-MEDIA </span> タグ </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34">The <span class="codeph"> オーディオ </span> および <span class="codeph"> ビデオ </span> の属性 <span class="codeph"> EXT-X-STREAM-INF </span> タグ </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> TVSDK 代替オーディオ </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
