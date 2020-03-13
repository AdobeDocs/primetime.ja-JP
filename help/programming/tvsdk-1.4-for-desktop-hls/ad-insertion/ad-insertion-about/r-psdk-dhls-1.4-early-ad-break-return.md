---
description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-description: ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。
seo-title: 早期の広告ブレークリターンの実装
title: 早期の広告ブレークリターンの実装
uuid: 984b6ed0-c929-49a3-9553-e30d1a7758ed
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 早期の広告ブレークリターンの実装{#implementing-an-early-ad-break-return}

ライブストリーム広告の挿入の場合、時間内のすべての広告が再生されて完了する前に、広告の時間を終了する必要がある場合があります。

>[!NOTE] {othertype=&quot;前提条件&quot;}
>
>スプライスのアウト/イン広告マーカー(、、および `#EXT-X-CUE-OUT`)をサブスクライ `#EXT-X-CUE-IN`ブする必要があ `#EXT-X-CUE`ります。

以下に、考慮すべき要件を示します。

* リニアストリームまたはFER `EXT-X-CUE-IN` ストリームに表示される（または同等のマーカータグ）などのマーカーを解析します。

   マーカーを広告の早期リターンポイントのマーカーとして登録します。 再生中は、こ `adBreaks` のマーカーの位置までのみ再生されます。この位置は、先頭のマーカーでマークされ `adBreak` ているマーカーの長さを上書き `EXE-X-CUE-OUT` します。

* 同じマーカ `EXT-X-CUE-IN` ーに2つのマーカー `EXT-X-CUE-OUT` が存在する場合、最初に表示 `EXT-X-CUE-IN` されるマーカーがカウントされます。

* マーカーがタ `EXE-X-CUE-IN` イムラインに表示され、先頭にマーカー `EXT-X-CUE-OUT` がない場合、マ `EXE-X-CUE-IN` ーカーは破棄されます。

   ライブストリームで、先頭のマーカーがウ `EXT-X-CUE-OUT` ィンドウの外に移動したとき、TVSDKは応答しません。

* 広告の時間から早い時点で再来訪がある場合、広告の時間が終了すると想定されていた時点で再生ヘッドが元の位置に戻り、その位置からメインコンテンツの再生が再開されるまで、が再生されます。 `adBreak`

## SpliceOutとSpliceIn {#section_36DD55BA58084E21BD3DC039BB245C82}

`SpliceOut` マーカ `SpliceIn` ーは、広告の時間の開始と終了を示します。 マーカーの種類の `SpliceOut` 長さはゼロ `EXE-X-CUE` で、マーカーの種類は広 `SpliceIn` 告の時 `EXE-X-CUE` 間の終わりを示します。 1つのタグに表示され、タイプによって異なります。

**異なるタイプの1つのマーカー**

例えば、異なるタイプのマーカーを1つ示します。

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

異なるタイプの1つのマーカーの例では、タイプの継続時間がゼロの場合、 `SpliceOut` とは各広告の時間 `SpliceOut` に対し `SpliceIn` て連携して機能する必要があります。 現在、デュレー `SpliceOut` ションがゼロ以外で、ペアリングマーカーが不要なマーカーが `SpliceIn` 一般的です。

**2つの別々のマーカー**

より一般的なシナリオは、 `SpliceOut` ゼロ以外の期間のマーカーで、ペアリングマーカーは不要 `SpliceIn` です。 ここで、ペアリングマ `SpliceIn` ーカーは、広告の時間の再生中に広告の時間の終わりをマークしますが、広告の時間はマーカーの位置で短く切り取られ、メインコンテンツはこの位 `SpliceIn` 置で再生を開始します。

例えば、次の2つのマーカーが別々に表示されます。

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

