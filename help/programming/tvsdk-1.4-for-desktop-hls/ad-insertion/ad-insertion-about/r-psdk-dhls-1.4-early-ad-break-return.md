---
description: ライブストリーム広告の挿入の場合、ブレーク内のすべての広告が最後まで再生される前に、広告ブレークから終了する必要が生じる場合があります。
title: 早期広告ブレークリターンの実装
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# 早期広告ブレークリターンの実装{#implementing-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、ブレーク内のすべての広告が最後まで再生される前に、広告ブレークから終了する必要が生じる場合があります。

>[!NOTE]
>
>スプライスアウト/イン広告マーカー ( `#EXT-X-CUE-OUT`, `#EXT-X-CUE-IN`、および `#EXT-X-CUE`) をクリックします。

以下に、考慮すべき要件を示します。

* マーカーの解析（例： ） `EXT-X-CUE-IN` （または同等のマーカータグ）が含まれ、線形ストリームまたは FER ストリームに表示されます。

  マーカーを広告の早いリターンポイントのマーカーとして登録します。 再生のみ `adBreaks` 再生中にこのマーカー位置まで ( `adBreak` 先頭に立つ `EXE-X-CUE-OUT` マーカー。

* 2 つの場合 `EXT-X-CUE-IN` 同じに対してマーカーが存在する `EXT-X-CUE-OUT` 最初の `EXT-X-CUE-IN` 表示されるマーカーは、カウントされるマーカーです。

* 次の場合、 `EXE-X-CUE-IN` マーカーは、先頭に `EXT-X-CUE-OUT` マーカー、 `EXE-X-CUE-IN` マーカーが破棄されました。

  ライブストリーム内で、 `EXT-X-CUE-OUT` マーカーがウィンドウの外に移動したとき、 TVSDK は応答しません。

* 広告ブレークからの早期のリターンがある場合、 `adBreak` 広告の時間が終了すると想定されていたときに再生ヘッドが元の位置に戻り、その位置からメインコンテンツの再生を再開するまで再生されます。

## SpliceOut と SpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` および `SpliceIn` マーカーは、広告ブレークの開始と終了をマークします。 期間 `SpliceOut` のタイプ `EXE-X-CUE` マーカーがゼロで、 `SpliceIn` のタイプ `EXE-X-CUE` マーカーは、広告ブレークの終わりをマークします。 1 つのタグ内に出現し、タイプごとに異なります。

**異なるタイプの 1 つのマーカー**

例えば、異なるタイプのマーカーが 1 つあるとします。

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

異なるタイプのサンプルを持つ 1 つのマーカーで、 `SpliceOut` type がゼロの場合、 `SpliceOut` および `SpliceIn` は、広告の時間ごとに連携して動作する必要があります。 現在、 `SpliceOut` ゼロ以外の時間で組み合わせが不要なマーカー `SpliceIn` マーカーの方が一般的です。

**2 つの個別のマーカー**

より一般的なシナリオは次のとおりです。 `SpliceOut` 時間がゼロでないマーカーで、ペアリングを必要としないもの `SpliceIn` マーカー。 ここでは、組み合わせ `SpliceIn` マーカーは、広告ブレークの再生中に広告ブレークの終わりをマークしますが、広告ブレークは `SpliceIn` マーカーの位置に配置され、メインコンテンツの再生がこの位置から開始されます。

例えば、次に 2 つの個別のマーカーを示します。

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
