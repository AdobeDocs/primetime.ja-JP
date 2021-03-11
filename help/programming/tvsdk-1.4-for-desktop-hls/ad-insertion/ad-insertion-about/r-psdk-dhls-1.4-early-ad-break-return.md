---
description: ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。
title: 早い広告の時間のリターンの実装
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# 早い広告ブレークのリターンの実装{#implementing-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、広告の時間内のすべての広告が最後まで再生される前に、広告の時間を終了する必要がある場合があります。

>[!NOTE]
>
>スプライスの広告マーカー(`#EXT-X-CUE-OUT`、`#EXT-X-CUE-IN`、`#EXT-X-CUE`)をサブスクライブする必要があります。

以下に、考慮すべき要件を示します。

* `EXT-X-CUE-IN`（または同等のマーカータグ）など、リニアストリームやFERストリームに出現するマーカーを解析します。

   マーカーを広告の初期のリターンポイントのマーカーとして登録します。 再生中にこのマーカー位置まで`adBreaks`のみを再生します。これは、先頭の`EXE-X-CUE-OUT`マーカーでマークされた`adBreak`の長さに優先します。

* 同じ`EXT-X-CUE-OUT`マーカーに対して2つの`EXT-X-CUE-IN`マーカーが存在する場合、最初に表示される`EXT-X-CUE-IN`マーカーがカウントされます。

* `EXE-X-CUE-IN`マーカーがタイムラインに表示され、先頭の`EXT-X-CUE-OUT`マーカーがない場合、`EXE-X-CUE-IN`マーカーは破棄されます。

   ライブストリームでは、先頭の`EXT-X-CUE-OUT`マーカーがウィンドウ外に移動した直後の場合、TVSDKはそれに応答しません。

* 広告の時間から早いリターンがある場合、`adBreak`は、広告の時間が終了すると想定されていた時点で再生ヘッドが元の位置に戻り、その位置からメインコンテンツの再生を再開するまで再生します。

## SpliceOutとSpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` および `SpliceIn` マーカーは、広告の時間の開始と終了を示します。`EXE-X-CUE`マーカーの`SpliceOut`タイプの長さは0で、`SpliceIn`タイプの`EXE-X-CUE`マーカーは広告の時間の終わりを示します。 1つのタグに表示され、タイプによって異なります。

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

異なるタイプの1つのマーカーの例では、`SpliceOut`タイプの継続時間がゼロの場合、広告の時間ごとに`SpliceOut`と`SpliceIn`が連動する必要があります。 現在、ゼロ以外の長さの`SpliceOut`マーカーで、`SpliceIn`マーカーのペアを必要としないのが、より一般的です。

**2つの個別のマーカー**

より一般的なシナリオは、ゼロ以外の長さの`SpliceOut`マーカーで、ペア`SpliceIn`マーカーは不要です。 ここで、ペア`SpliceIn`マーカーは、広告の時間の再生中に広告の時間の終わりを示しますが、広告の時間は`SpliceIn`マーカーの位置で短くなり、この位置で再生するメインコンテンツ開始が短くなります。

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

