---
description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
seo-description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
seo-title: 早い広告の時間のリターンの実装
title: 早い広告の時間のリターンの実装
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# 早い広告の時間のリターンの実装{#implementing-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。

>[!NOTE]
>
>スプライス出力/入力広告マーカー(、、および `#EXT-X-CUE-OUT``#EXT-X-CUE-IN``#EXT-X-CUE`)を購読する必要があります。

以下に、考慮すべき要件を示します。

* リニアストリームまたはFERストリームに表示される `EXT-X-CUE-IN` （または同等のマーカータグ）などのマーカーを解析します。

   マーカーを広告の初期のリターンポイントのマーカーとして登録します。 再生中は、このマーカーの位置まで再生 `adBreaks` します。この位置は、先頭のマーカーでマークさ `adBreak` れた長さに優先し `EXE-X-CUE-OUT` ます。

* 同じマーカに2つの `EXT-X-CUE-IN` マーカが存在する場合は、最初に表示されるマーカがカウントされ `EXT-X-CUE-OUT``EXT-X-CUE-IN` るマーカです。

* マーカーがタイムラインに表示されているときに先頭のマーカーがない場合、そのマーカー `EXE-X-CUE-IN``EXT-X-CUE-OUT``EXE-X-CUE-IN` は破棄されます。

   ライブストリームでは、先頭の `EXT-X-CUE-OUT` マーカーがウィンドウの外に移動した直後の場合、TVSDKはこのマーカーに応答しません。

* 広告の時間から早いリターンがある場合、広告の時間が終了すると想定されていたときに再生ヘッドが元の位置に戻り、その位置からメインコンテンツの再生が再開されるまで再生されます。 `adBreak`

## SpliceOutとSpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` および `SpliceIn` マーカーは、広告の時間の開始と終了を示します。 マーカーの `SpliceOut` タイプの継続時間は0になり、マーカーの `EXE-X-CUE` タイプは広告の時間の終わりを `SpliceIn``EXE-X-CUE` 示します。 1つのタグに表示され、タイプによって異なります。

**1つのマーカーに異なるタイプ**

例えば、次に示すのは、異なるタイプのマーカーの1つです。

```
#EXTM3U#EXT-X-TARGETDURATION:10
#EXT-X-VERSION:3
#EXT-X-MEDIA-SEQUENCE:44
  
#EXTINF:9.9,
https://server-host/path/file44.ts
#EXTINF:4.2,
https://server-host/path/file45.ts
  
#EXT-X-CUE:TYPE="SpliceOut",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138",AVAIL-NUM="1",AVAILS-EXPECTED="10"
#EXTINF:5.8,
https://server-host/path/file46.ts
#EXTINF:9.9,
https://server-host/path/file47.ts
...
#EXTINF:9.9,
https://server-host/path/file56.ts
#EXTINF:4.2,
https://server-host/path/file57.ts
#EXT-X-CUE:TYPE="SpliceIn",ID="1",DURATION="0",TIME="266.198",PROGRAM-ID="138"
#EXTINF:9.9,
https://server-host/path/file58.ts
```

異なるタイプの1つのマーカーの例では、タイプの継続時間がゼロの場合、 `SpliceOut` とは各広告の時間に対して連携して動作する `SpliceOut` 必要 `SpliceIn` があります。 現在、ゼロ以外の長さのマーカーで、ペアリングマーカーを必要としないものが、より一般的 `SpliceOut``SpliceIn` です。

**2つの個別のマーカー**

より一般的なシナリオは、ゼロ以外の長さのマーカーで、ペアリングの `SpliceOut``SpliceIn` マーカーは必要ありません。 ここで、ペアリングマーカーは、広告の時間の再生中に広告の時間の終わりを示しますが、広告の時間はマーカーの位置で短くなり、 `SpliceIn``SpliceIn` この位置で再生するメインコンテンツ開始が短くなります。

例えば、次の2つのマーカーは別々に表示されます。

```
#EXT-X-CUE-OUT:ID=105,DURATION=30.0,TIME=1081.08
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589090425811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589150485811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589210545811,format=m3u8-aapl-v4)
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589270605811,format=m3u8-aapl-v4)
#EXT-X-CUE-IN:ID=105,TIME=1105.104
#EXTINF:6.006000,no-desc
/live/hls/nbc-fer/QualityLevels(2200000)/Fragments(video=14332589330665811,format=m3u8-aapl-v4)
```

