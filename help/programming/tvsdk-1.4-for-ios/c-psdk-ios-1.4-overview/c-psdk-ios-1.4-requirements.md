---
description: TVSDKには、メディアコンテンツ、マニフェストコンテンツおよびソフトウェアバージョンに固有のプロパティが必要です。
seo-description: TVSDKには、メディアコンテンツ、マニフェストコンテンツおよびソフトウェアバージョンに固有のプロパティが必要です。
seo-title: 要件
title: 要件
uuid: 7e5fb176-4c3f-4c12-9080-3afced28627b
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 要件 {#requirements}

TVSDKには、メディアコンテンツ、マニフェストコンテンツおよびソフトウェアバージョンに固有のプロパティが必要です。

## システムとソフトウェアの要件 {#section_61C32A0209C44230B392B113B85643EE}

TVSDKを使用するには、お使いのハードウェア、オペレーティングシステム、アプリケーションのバージョンがすべて、以下に示す最小要件を満たしていることを確認します。

オペレーティングシステム：iOS 6.0以降

## コンテンツとマニフェストの要件 {#section_05FA02E2189742008DA09D87E66DCAB7}

DRM暗号化キーを含む、ストリームおよび再生リスト（マニフェスト）の制限と要件を確認します。

| コンテンツセグメントのキーフレーム | 各コンテンツセグメントは、キーフレームで始まる必要があります。 |
|---|---|
| ライブ/リニアビデオのシーケンス番号 | メインコンテンツのすべてのビットレートレンディションが、同時に一致する必要があります。 |

## #EXT-X-VERSIONの要件 {#section_C03D3DCE1D244E26BBD2C1D7144FDFBD}

ファイル内ののバ `#EXT-X-VERSION` ージョ [!DNL .m3u8] ンは、アプリケーションで使用できる機能と、プレイリスト/マニフェストで `EXT` 有効なタグに影響を与えます。

HLSプロトコルのバージョンを指定する `#EXT-X-VERSION` タグに関する情報を次に示します。

* バージョンは、HLSプレイリストの機能と属性に一致する必要があります。そうしないと、再生エラーが発生する可能性があります。

   詳しくは、 [HTTPライブストリーミングの仕様を参照してください](https://datatracker.ietf.org/doc/draft-pantos-http-live-streaming/?include_text=1)。
* タグがマスター再生リストまたはメディア再生リストに含まれていない場合、またはバージョンが指定されていない場合は、デフォルトでバージョン1が使用されます。 バージョン1に準拠しないコンテンツは再生されません。
* TVSDKベースのクライアントでの再生には、少なくともバージョン2を使用することをお勧めします。

クライアントおよびサーバーは、次の方法でバージョンを実装する必要があります。

<table id="table_62EB98EDD9DE49EC84CB1C7D59BC40E6"> 
 <thead> 
  <tr> 
   <th colname="1" class="entry"> 少なくともこのバージョンを使用する </th> 
   <th colname="2" class="entry"> これらの機能を使用するには </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:2 </span> </td> 
   <td colname="2"> EXT-X-KEYタ <span class="codeph"> グのIV属性 </span> 。 </td> 
  </tr> 
  <tr> 
   <td colname="1"> <span class="codeph"> EXT-X-VERSION:3 </span> </td> 
   <td colname="2"> 
    <ul id="ul_C9500D3F934848639C204BF248F139FF"> 
     <li id="li_535A7E3FABCB46FE872A7EA5DE2A1784">浮動小数点 <span class="codeph"> EXTINF期 </span> 間値 <p>期間タグ( <span class="codeph"> #EXTINF:バー </span>ジョン2の&lt;duration&gt;,&lt;title&gt;)は、整数値に丸められました。 バージョン3以降では、浮動小数点での長さと完全に一致する必要があります。 </p> </li> 
     <li id="li_8DF5E91F1D5D4E19894595E1FE0A5EDE"> 広告挿入やシームレスABRなどのTVSDK機能 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="1"> <p> <span class="codeph"> EXT-X-VERSION:4 </span> </p> </td> 
   <td colname="2"> <p> 
     <ul id="ul_99E24D013E3141308B5A57446A9B8033"> 
      <li id="li_F36E65ADD2CA451C82FF18DBD5667927">EXT- <span class="codeph"> X-BYTERANGEタ </span> グ </li> 
      <li id="li_8C653168A7B84D11AC233E7548A8D2EF">EXT-X-I-FRAME-STREAM-INFタ <span class="codeph"></span> グ </li> 
      <li id="li_2922B34717CB4F6189068529CDBE6D10">EXT- <span class="codeph"> X-I-FRAMES-ONLYタ </span> グ </li> 
      <li id="li_D015D78E217641D7867EB509E9F9EEE2">EXT- <span class="codeph"> X-MEDIAタ </span> グ </li> 
      <li id="li_CA068EA381984F5497FE67617CA8BB34"><span class="codeph"> EXT-X-STREAM-INF </span> タ <span class="codeph"> グのAUDIO属性とVIDEO属 </span><span class="codeph"></span> 性 </li> 
      <li id="li_EE78CC7D194A4EB2897F9AE8E4B081B8"> TVSDK代替オーディオ </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
