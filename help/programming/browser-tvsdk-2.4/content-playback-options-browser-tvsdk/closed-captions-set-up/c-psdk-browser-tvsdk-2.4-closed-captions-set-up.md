---
description: クローズドキャプションは、サウンドが聞こえない場合やビューアが聞きにくい場合に、ビデオのオーディオ部分をテキストとして画面に表示します。
title: クローズドキャプションの操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# クローズドキャプションの操作{#work-with-closed-captions}

クローズドキャプションは、サウンドが聞こえない場合やビューアが聞きにくい場合に、ビデオのオーディオ部分をテキストとして画面に表示します。

クローズドキャプションは通常、オーディオと同じ言語で、背景サウンドもテキストとして表示されますが、サブタイトルは通常別の言語で、背景サウンドは含まれません。

ブラウザー TVSDK は、次の形式のレンダリングをサポートしています。

* 608 および 708 クローズドキャプション。MPEG-2 ビデオストリームのデータパケットとして HLS を介したビデオ転送ストリームの一部として配信される場合。
* WebVTT キャプションファイル。HLS 仕様で定義されている M3U8 マニフェストファイルから参照されます。 Primetime Player では、クローズドキャプショントラックとして自動的に使用できます。

次の操作が可能です。

* 現在のトラックとなる使用可能なキャプショントラックを選択し、使用可能な追加のトラックを示すイベントをリッスンします。
* クローズドキャプションのオン/オフ（表示/非表示）を切り替えるには、 `MediaPlayer` インターフェイス。
* クローズドキャプションが基になるビデオエンジンによってどのようにレンダリングされるかを指定するスタイル設定オプションを選択します。 以下を使用します。 `MediaPlayerItem` インターフェイスを使用して、フォントやフォントカラーなどの書式を選択できます。
