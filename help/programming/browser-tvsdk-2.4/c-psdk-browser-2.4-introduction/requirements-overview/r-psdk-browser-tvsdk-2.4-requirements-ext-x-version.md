---
description: .m3u8ファイル内の「#」EXT-X-VERSIONのバージョンは、アプリケーションで使用可能な機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
title: '''#''EXT-X-VERSIONの要件'
exl-id: 1b7c205b-c6b1-416f-885a-d1cd23d8e803
source-git-commit: 8610792a7410dab59d42ab7771b534c2c1670ad2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# `#`EXT-X-VERSIONの要件{#ext-x-version-requirements}

.m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用可能な機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

HLSプロトコルのバージョンを指定する`#EXT-X-VERSION`タグに関する情報を以下に示します。

* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。 詳しくは、[HTTPライブストリーミングの仕様](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)を参照してください。
* Adobeは、ブラウザーTVSDKベースのクライアントでの再生に少なくともバージョン2を使用することをお勧めします。

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
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3  </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点<span class="codeph"> EXTINF </span>デュレーション値 <p>期間タグ( <span class="codeph"> #EXTINF:バージョン2の</span>&lt;duration&gt;,&lt;title&gt;)は整数値に丸められました。 バージョン3以降では、浮動小数点で正確に指定する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:4  </span> </td> 
   <td colname="2"> 
    <ul id="ul_3355A6CBBE2141DDB92660BB4B604D70"> 
     <li id="li_A7783AFF99854EFBBAECD2967E4CBF2B"><span class="codeph"> EXT-X-MEDIA </span>タグ </li> 
     <li id="li_15AE652F33C1454AA90DDC65E7D6C2FD"><span class="codeph"> EXT-X-STREAM-INF </span>タグの<span class="codeph"> AUDIO </span>および<span class="codeph"> VIDEO </span>属性 </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
