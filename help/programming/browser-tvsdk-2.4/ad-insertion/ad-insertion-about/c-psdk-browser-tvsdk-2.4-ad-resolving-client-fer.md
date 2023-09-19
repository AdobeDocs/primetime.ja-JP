---
description: 完全なイベント再生 (FER) コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することで、VOD に変換されたライブストリームです。 ストリームは、広告キューマーカーを保持します。
title: FER 広告の解決と挿入
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# FER 広告の解決と挿入{#fer-ad-resolving-and-insertion}

完全なイベント再生 (FER) コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することで、VOD に変換されたライブストリームです。 ストリームは、広告キューマーカーを保持します。

ブラウザー TVSDK は、FER ストリームを VOD として扱うので、デフォルトでは、広告シグナリングモードは `SERVER_MAP`. ただし、ストリームは広告キューマーカーを保持するので、広告シグナリングモードをに設定できます。 `MANIFEST_CUES`：広告挿入に広告キューマーカーを使用できます。

FER ストリームのキューマーカーを使用して広告挿入をオンにするには：

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

FER 広告の解決と挿入の動作は、ライブ広告の解決と挿入に似ています。 ブラウザー TVSDK は、以下を実行します。

1. コンテンツの先頭にプリロール広告を挿入します。
1. マニフェストで定義されているキューポイントで指定されている広告を解決します。
1. メインコンテンツの一部を、同じ期間の広告の時間に置き換えます。
1. 必要に応じて、バーチャルタイムラインを再計算します。

**制限：** ブラウザー TVSDK は、HLS FER ストリーム再生のみをサポートします。 また、MP4 ミッドロール広告は、FER ストリームではサポートされていません。
