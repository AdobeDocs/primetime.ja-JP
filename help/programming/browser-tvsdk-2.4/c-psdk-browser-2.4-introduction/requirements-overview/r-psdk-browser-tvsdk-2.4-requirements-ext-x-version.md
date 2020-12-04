---
description: .m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
seo-description: .m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
seo-title: '#EXT-X-VERSIONの要件'
title: '#EXT-X-VERSIONの要件'
uuid: 8d22930f-4faf-4a40-b1f0-507886cd8938
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# #EXT-X-VERSION要件{#ext-x-version-requirements}

.m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

`#EXT-X-VERSION`タグに関する情報を次に示します。このタグはHLSプロトコルのバージョンを指定します。

* バージョンは、HLSプレイリストの機能と属性と一致する必要があります。そうしないと、再生エラーが発生する場合があります。 詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* Adobeでは、ブラウザーTVSDKベースのクライアントでの再生に少なくともバージョン2を使用することをお勧めします。

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点<span class="codeph"> EXTINF </span>期間値 <p>期間タグ( <span class="codeph"> #EXTINF:バージョン2の</span>&lt;duration&gt;,&lt;title&gt;)は、整数値に丸められました。 バージョン3以降では、浮動小数点と完全に一致する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4  </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B"><span class="codeph"> EXT-X-MEDIA </span>タグ </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD"><span class="codeph"> AUDIO </span>および<span class="codeph"> VIDEO </span>属性（<span class="codeph"> EXT-X-STREAM-INF </span>タグの属性） </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

