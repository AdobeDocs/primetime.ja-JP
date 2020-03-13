---
description: .m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
seo-description: .m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。
seo-title: '#EXT-X-VERSIONの要件'
title: '#EXT-X-VERSIONの要件'
uuid: c862df4a-88ba-4497-8b7c-b83fcb34b8bb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# #EXT-X-VERSIONの要件{#ext-x-version-requirements}

.m3u8ファイル内の#EXT-X-VERSIONのバージョンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで有効なEXTタグに影響します。

<!--<a id="section_8850183988124049A001758F117AD3A6"></a>-->

HLSプロトコルのバージョンを指定する `#EXT-X-VERSION` タグに関する情報を次に示します。

* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。

   詳しくは、 [HTTPライブストリーミングの仕様を参照してください](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)。
* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。

   詳しくは、 [HTTPライブストリーミングの仕様を参照してください](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)。
* ベースのクライアントでの再生には、少なくともバージョン2を使用することをお勧めします。

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
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF期 </span> 間値 <p>期間タグ( <span class="codeph"> #EXTINF:バー </span>ジョン2の&lt;duration&gt;,&lt;title&gt;)は、整数値に丸められました。 バージョン3以降では、浮動小数点での長さと完全に一致する必要があります。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_83D61E909D0C413FBDAB7A4A0BE1F03C"> 
      <li id="li_5071F2BE2DB74BBFB1F23B3B30C5CFD6">EXT- <span class="codeph"> X-BYTERANGEタ </span> グ </li> 
      <li id="li_A093F448567D475AB44656D4600BCBD6">EXT-X-I-FRAME-STREAM-INFタ <span class="codeph"></span> グ </li> 
      <li id="li_1084AE3B10FD4EB387D25EEDDFBBC8CD">EXT- <span class="codeph"> X-I-FRAMES-ONLYタ </span> グ </li> 
      <li id="li_4FEFA36E300C403DBB77BB4DA46DB4EB">EXT- <span class="codeph"> X-MEDIAタ </span> グ </li> 
      <li id="li_E53D81AED45C47AEA346FA3A1B191E5C"><span class="codeph"> EXT-X-STREAM-INF </span> タ <span class="codeph"> グのAUDIO属性とVIDEO属 </span><span class="codeph"></span> 性 </li> 
      <li id="li_2E99A4971B8046F3845CF3D4D363CCCF">TVSDK代替オーディオ </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>

