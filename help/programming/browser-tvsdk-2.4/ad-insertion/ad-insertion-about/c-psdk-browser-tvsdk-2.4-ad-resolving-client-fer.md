---
description: Full Event Replay(FER)コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することでVODに変換されたライブストリームです。 ストリームは広告キューマーカーを保持します。
seo-description: Full Event Replay(FER)コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することでVODに変換されたライブストリームです。 ストリームは広告キューマーカーを保持します。
seo-title: FER広告の解決と挿入
title: FER広告の解決と挿入
uuid: 85da0e92-17fe-4001-a53c-085dadd09756
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# FER広告の解決と挿入{#fer-ad-resolving-and-insertion}

Full Event Replay(FER)コンテンツは、マニフェストファイルの末尾に#EXT-X-ENDLISTタグを追加することでVODに変換されたライブストリームです。 ストリームは広告キューマーカーを保持します。

ブラウザーTVSDKは、FERストリームをVODとして扱うので、デフォルトでは広告シグナリングモードはで `SERVER_MAP`す。 ただし、ストリームは広告キューマーカーを保持するので、広告シグナリングモードをに設定して、広告 `MANIFEST_CUES`挿入に広告キューマーカーを使用できます。

FERストリームのキューマーカーを使用して広告挿入を有効にするには：

```js
var config = new AdobePSDK.MediaPlayerItemConfig(); 
config.adSignalingMode = AdobePSDK.AdSignalingMode.MANIFEST_CUES; 
player.replaceCurrentResource(mediaResource, config);
```

FER広告の解決と挿入の動作は、ライブ広告の解決と挿入に似ています。 ブラウザーTVSDKは、次の処理を行います。

1. コンテンツの先頭にプリロール広告を挿入します。
1. マニフェストで定義されているキューポイントで指定された広告を解決します。
1. メインコンテンツの一部を同じ期間の広告の時間に置き換えます
1. 必要に応じて、バーチャルタイムラインを再計算します。

**制限：** ブラウザーTVSDKは、HLS FERストリームの再生のみをサポートします。 また、MP4ミッドロール広告はFERストリームではサポートされません。
