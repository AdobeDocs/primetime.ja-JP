---
description: 適切に設定されたpttimelineクエリパラメーターで新しい広告挿入リクエストをマニフェストサーバーに送信し、VODタイムラインを置き換えます。
seo-description: 適切に設定されたpttimelineクエリパラメーターで新しい広告挿入リクエストをマニフェストサーバーに送信し、VODタイムラインを置き換えます。
seo-title: VODタイムラインの置き換え
title: VODタイムラインの置き換え
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: e437f4143fb939f46d106c64efc391137c33fe17
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---


# VODタイムラインの置き換え{#replace-a-vod-timeline}

適切に設定されたpttimelineクエリパラメーターで新しい広告挿入リクエストをマニフェストサーバーに送信し、VODタイムラインを置き換えます。

1. 通常の方法で広告挿入リクエストを準備します。
1. `ptcueformat`クエリパラメーターをDPIScte35に設定します。
1. 必要に応じて、`enableC3`クエリパラメーターをtrueまたはfalseに設定します。
1. VODタイムライン形式を使用して`pttimeline`パラメーターを作成します。
   1. `duration = 0`と`number_of_lots = 1`を使用して、各コンテンツブロック（チャプタ）を指定します。
   1. 通常どおり各広告ブロックを指定しますが、`lots = 0`を設定して広告の時間を削除します。 （M3U8ファイルの）広告の時間の長さを使用するように`duration = 0`を設定します。

## 例：VODタイムラインの置き換え

この例では、VODコンテンツが`Original.m3u8`にあり、タイムラインが`C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`であると仮定しています

次のマニフェストサーバーリクエストは、`Original.m3u8`内のブレークを30秒のプリロールで置き換え、その後それぞれ2分間の継続時間が続きます。

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

次のマニフェストサーバーリクエストは、`Original.m3u8`の中断を削除し、30秒のプリロールと30秒のポストロールを追加します。

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
