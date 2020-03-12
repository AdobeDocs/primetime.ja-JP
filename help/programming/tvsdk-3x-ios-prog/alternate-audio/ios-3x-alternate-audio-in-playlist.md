---
description: 代替オーディオ（遅延バインディング）を使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ユーザはビデオの再生時に言語トラックを選択できます。
seo-description: 代替オーディオ（遅延バインディング）を使用すると、ビデオトラックで使用可能なオーディオトラックを切り替えることができます。 これにより、ユーザはビデオの再生時に言語トラックを選択できます。
seo-title: プレイリスト内の代替オーディオトラック
title: プレイリスト内の代替オーディオトラック
uuid: 6241d3e4-6e07-44fb-bc0e-5d49d1a76824
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# プレイリスト内の代替オーディオトラック {#section_BC8C1C74A5A24A8CA68C1E7E721EE742}

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
