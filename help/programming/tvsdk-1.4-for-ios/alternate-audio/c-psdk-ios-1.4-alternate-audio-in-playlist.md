---
description: ビデオのプレイリストは、メインのビデオコンテンツに対して、無制限数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にユーザーがデバイス上で異なるトラックを切り替えることを許可したりできます。
title: プレイリスト内の代替オーディオトラック
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# プレイリスト内の代替オーディオトラック{#alternate-audio-tracks-in-the-playlist}

ビデオのプレイリストは、メインのビデオコンテンツに対して、無制限数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にユーザーがデバイス上で異なるトラックを切り替えることを許可したりできます。

代替オーディオトラック（遅延バインディングオーディオ）を使用すると、HTTP ビデオストリーム（ライブ/リニアおよび VOD）用に複数の言語トラックを切り替えることができます。また、各オーディオトラック用にビデオを変更、複製、再パッケージ化する必要はありません。 アセットの初期パッケージ化の前または後に、1 つのビデオアセットに対して複数の言語トラックを指定できます。

>[!TIP]
>
>代替オーディオをメインメディアのビデオトラックとミキシングするには、代替トラックのタイムスタンプがメイントラックのオーディオのタイムスタンプと一致している必要があります。

代替オーディオトラックを使用し、広告を組み込む場合は、次の要件が適用されます。

* メインコンテンツに代替オーディオトラックがある場合、広告には少なくとも 1 つのオーディオ専用ストリームが必要です。
* 広告のオーディオ専用ストリームの各セグメントの長さは、広告のビデオストリームのセグメントの長さと等しくする必要があります。

メインのオーディオトラックは、 `default` ラベル。 代替オーディオストリームのメタデータは、 `#EXT-X-MEDIA` タグと `TYPE=AUDIO`.

例えば、複数の代替オーディオストリームを指定する M3U8 マニフェストは、次のようになります。

```
#EXTM3U
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 1",
 AUTOSELECT=YES,DEFAULT=YES
#EXT-X-MEDIA:TYPE=AUDIO,GROUP-ID="bipbop_audio",LANGUAGE="eng",NAME="BipBop Audio 2",
 AUTOSELECT=NO,DEFAULT=NO,URI="alternate_audio_aac/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="eng",URI="subtitles/eng/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="English (Forced)",DEFAULT=YES,
 AUTOSELECT=YES,FORCED=YES,LANGUAGE="eng",URI="subtitles/eng_forced/prog_index.m3u8"
#EXT-X-MEDIA:TYPE=SUBTITLES,GROUP-ID="subs",NAME="Français",AUTOSELECT=YES,FORCED=NO,
 LANGUAGE="fra",URI="subtitles/fra/prog_index.m3u8"
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=263851,CODECS="mp4a.40.2, avc1.4d400d",
 RESOLUTION=416x234,AUDIO="bipbop_audio",SUBTITLES="subs" 
gear1/prog_index.m3u8
#EXT-X-STREAM-INF:PROGRAM-ID=1,BANDWIDTH=577610,CODECS="mp4a.40.2, avc1.4d401e",
 RESOLUTION=640x360,AUDIO="bipbop_audio",SUBTITLES="subs"
gear2/prog_index.m3u8
...
```
