---
description: .m3u8ファイル内の「#」EXT-X-VERSIONのバージョンは、アプリケーションで使用可能な機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
title: EXT-X-VERSIONの要件
exl-id: ee778fe1-d050-4c90-af8d-6600fff72e52
source-git-commit: 8610792a7410dab59d42ab7771b534c2c1670ad2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# `#`EXT-X-VERSIONの要件{#ext-x-version-requirements}

.m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用可能な機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

HLSプロトコルのバージョンを指定する`#EXT-X-VERSION`タグに関する情報を以下に示します。

* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。

   詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。

   詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* Adobeでは、ベースのクライアントでの再生にバージョン2以上を使用することをお勧めします。

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2  </span> </td> 
   <td colname="2"> <span class="codeph"> EXT-X-KEY </span>タグのIV属性。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点<span class="codeph"> EXTINF </span>デュレーション値 <p>期間タグ( <span class="codeph"> #EXTINF:バージョン2の</span>&lt;duration&gt;,&lt;title&gt;)は整数値に丸められました。 バージョン3以降では、浮動小数点で正確に指定する必要があります。 </p> </li> 
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
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C"><span class="codeph"> EXT-X-STREAM-INF </span>タグの<span class="codeph"> AUDIO </span>および<span class="codeph"> VIDEO </span>属性 </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">TVSDK代替オーディオ </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
