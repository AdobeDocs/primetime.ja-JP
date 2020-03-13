---
description: ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。
seo-description: ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。
seo-title: プレイリスト内の代替オーディオトラック
title: プレイリスト内の代替オーディオトラック
uuid: e134cc46-5cd3-4c3c-a6ef-5ae54a2108ce
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# プレイリスト内の代替オーディオトラック {#alternate-audio-tracks-in-the-playlist}

ビデオのプレイリストは、メインビデオコンテンツに対して、無制限に数の代替オーディオトラックを指定できます。 例えば、ビデオコンテンツに異なる言語を追加したり、コンテンツの再生中にデバイス上の異なるトラックを切り替えたりできます。

代替オーディオトラックを使用すると、HTTPビデオストリーム（ライブ/リニアおよびVOD）用に複数の言語トラックを切り替えることができ、各オーディオトラックのビデオを変更、複製または再パッケージ化する必要がありません。 アセットの初期パッケージ化の前後に、ビデオアセットに対して複数の言語トラックを指定できます。

>[!IMPORTANT]
>
>代替オーディオをメインメディアのビデオトラックと混合するには、代替トラックのタイムスタンプがメイントラックのオーディオのタイムスタンプと一致する必要があります。

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
