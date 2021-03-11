---
description: .m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
title: '#EXT-X-VERSIONの要件'
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# #EXT-X-VERSION要件{#ext-x-version-requirements}

.m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

`#EXT-X-VERSION`タグに関する情報を次に示します。このタグはHLSプロトコルのバージョンを指定します。

* バージョンは、HLSプレイリストの機能と属性と一致する必要があります。そうしないと、再生エラーが発生する場合があります。

   詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* バージョンは、HLSプレイリストの機能と属性と一致する必要があります。そうしないと、再生エラーが発生する場合があります。

   詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* Adobeでは、ベースのクライアントでの再生に少なくともバージョン2を使用することをお勧めします。

   クライアントとサーバーは、次の方法でバージョンを実装する必要があります。

<table frame="all" colsep="1" rowsep="1" id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 少なくともこのバージョンを使用する </th> 
   <th colname="2" class="entry"> これらの機能を使用するには </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2  </span> </td> 
   <td colname="2"> <span class="codeph"> EXT-X-KEY </span>タグのIV属性。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点<span class="codeph"> EXTINF </span>期間値 <p>期間タグ( <span class="codeph"> #EXTINF:バージョン2の</span>&lt;duration&gt;,&lt;title&gt;)は、整数値に丸められました。 バージョン3以降では、浮動小数点と完全に一致する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4  </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6"><span class="codeph"> EXT-X-BYTERANGE </span>タグ </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6"><span class="codeph"> EXT-X-I-FRAME-STREAM-INF </span>タグ </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD"><span class="codeph"> EXT-X-I-FRAMES-ONLY </span>タグ </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB"><span class="codeph"> EXT-X-MEDIA </span>タグ </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C"><span class="codeph"> AUDIO </span>および<span class="codeph"> VIDEO </span>属性（<span class="codeph"> EXT-X-STREAM-INF </span>タグの属性） </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">TVSDK代替オーディオ </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

