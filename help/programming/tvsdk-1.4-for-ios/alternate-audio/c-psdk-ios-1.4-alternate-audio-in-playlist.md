---
description: ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。
seo-description: ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。
seo-title: プレイリスト内の代替オーディオトラック
title: プレイリスト内の代替オーディオトラック
uuid: 68f01375-9d57-4839-a1c0-7e022b374012
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# プレイリスト内の代替オーディオトラック{#alternate-audio-tracks-in-the-playlist}

ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。

代替オーディオトラック、つまり遅延バインディングオーディオを使用すると、HTTPビデオストリーム（ライブ/リニアおよびVOD）用に複数の言語トラックを切り替えることができ、各オーディオトラックのビデオを変更、複製または再パッケージ化する必要がありません。 アセットの初期パッケージ化の前後に、ビデオアセットに対して複数の言語トラックを指定できます。

>[!TIP]
>
>代替オーディオをメインメディアのビデオトラックと混合するには、代替トラックのタイムスタンプがメイントラックのオーディオのタイムスタンプと一致する必要があります。

代替オーディオトラックを使用し、広告を組み込む場合は、次の要件が適用されます。

* メインコンテンツに代替オーディオトラックが含まれる場合、広告には少なくとも1つのオーディオ専用ストリームが必要です。
* 広告のオーディオ専用ストリームの各セグメントの長さは、広告のビデオストリームのセグメントの長さと等しくなければなりません。

メインのオーディオトラックは、ラベルと共にオーディオトラックコレクションに含ま `default` れます。 代替オーディオストリームのメタデータは、のタグのプレイリストに `#EXT-X-MEDIA` 含まれま `TYPE=AUDIO`す。

例えば、複数の代替オーディオストリームを指定するM3U8マニフェストは、次のようになります。

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

