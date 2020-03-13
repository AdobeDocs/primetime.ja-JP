---
description: 適切に設定されたpttimelineクエリパラメーターを使用して、新しい広告挿入要求をマニフェストサーバーに送信し、VODタイムラインを置き換えます。
seo-description: 適切に設定されたpttimelineクエリパラメーターを使用して、新しい広告挿入要求をマニフェストサーバーに送信し、VODタイムラインを置き換えます。
seo-title: VODタイムラインの置き換え
title: VODタイムラインの置き換え
uuid: 17a6daa3-5ee5-48fb-8981-0d183aed0fe4
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# VODタイムラインの置き換え {#replace-a-vod-timeline}

適切に設定されたpttimelineクエリパラメーターを使用して、新しい広告挿入要求をマニフェストサーバーに送信し、VODタイムラインを置き換えます。

1. 通常の方法で広告挿入リクエストを準備します。
1. クエリパラメ `ptcueformat` ーターをDPIScte35に設定します。
1. 必要に応じて、 `enableC3` クエリパラメーターをtrueまたはfalseに設定します。
1. VODタイムライン形 `pttimeline` 式を使用して、パラメーターを作成します。
   1. 各コンテンツブロック（チャプター）をとと共に指 `duration = 0` 定しま `number_of_lots = 1`す。
   1. 通常どおり、各広告ブロックを指定しますが、時間を削 `lots = 0` 除するように設定します。 (M3U8 `duration = 0` ファイルの)広告の時間の継続時間を使用するように設定します。

## 例：VODタイムラインの置き換え

この例では、VODコンテンツが `Original.m3u8``C,120,1;B,60,2,m;C,120,1;B,60,2,m;C,120,1;`

次のマニフェストサーバーリクエストは、30秒のプ `Original.m3u8` リロールでの時間を2分ずつの時間で置き換えます。

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,120,4,m;C,0,1;B,120,4,m;C,0,1;
```

次のマニフェストサーバーリクエストは、での中断を削 `Original.m3u8` 除し、30秒のプリロールと30秒のポストロールを追加します。

```
https://manifest.auditude.com/auditude/variant/pubAsset/Original.m3u8?. . .&enableC3=false 
&pttimeline=B,30,2,p;C,0,1;B,0,0,m;C,0,1;B,0,0,m;C,0,1;B,30,2,t;
```
