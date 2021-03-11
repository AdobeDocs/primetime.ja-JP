---
description: フルイベント再生(FER)コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することで、VODに変換されたライブストリームです。 ストリームは広告キューマーカーを保持します。
title: FER広告の解決と挿入
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# FER広告解決と挿入{#fer-ad-resolving-and-insertion}

フルイベント再生(FER)コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することで、VODに変換されたライブストリームです。 ストリームは広告キューマーカーを保持します。

ブラウザーTVSDKは、FERストリームをVODとして扱うので、デフォルトでは広告シグナリングモードは`SERVER_MAP`です。 ただし、ストリームは広告キューマーカーを保持するので、広告シグナリングモードを`MANIFEST_CUES`に設定して、広告挿入に広告キューマーカーを使用できます。

FERストリームのキューマーカーを使用して広告挿入をオンにするには：

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

FER広告の解決と挿入の動作は、ライブ広告の解決と挿入に似ています。 ブラウザーTVSDKは、以下を実行します。

1. コンテンツの先頭にプリロール広告を挿入します。
1. マニフェストで定義されているキューポイントで指定されている広告を解決します。
1. メインコンテンツの一部を、同じ継続時間の広告の時間に置き換えます
1. 必要に応じて、バーチャルタイムラインを再計算します。

**制限：** ブラウザーTVSDKは、HLS FERストリーム再生のみをサポートします。また、MP4ミッドロール広告は、FERストリームではサポートされません。
