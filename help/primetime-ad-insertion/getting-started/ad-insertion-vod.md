---
title: VODにAd Insertionを使用
description: VODにAd Insertionを使用する
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# VODにAd Insertionを使用{#ad-insertion-vod}

PrimetimeAd Insertionは、標準のVAST 3.0以降またはVMAP 1.0以降の形式を使用して、複数のVODアセットへの広告挿入をサポートします。

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD（広告マップ） {#server-mapped-ads}

PrimetimeAd Insertionでは、VMAP形式で定義された広告タイムライン情報を使用して、再生開始前に広告を挿入するVOD挿入をサポートしています。  breakStart/breakEndビーコンなどのVMAP固有の広告トラッキングは、[広告トラッキング](set-up-ad-tracking.md)と共に配信されます。

## フルイベント再生(Ad Decisioningキュー付きVOD) {#full-event-replay}

PrimetimeAd Insertionは、以前に記録されたライブイベントの再生時など、コンテンツストリーム自体のキューを含む特殊なVODアセットもサポートします。 サポートする広告決定キュー（またはキュー形式）のタイプについて詳しくは、[ライブ/リニアでのAd Insertionの使用](ad-insertion-live-linear-stream.md)を参照してください。

複数の広告ブレークを含むVODアセットに対して、単一の広告リクエストシナリオと並行する複数の広告リクエストシナリオの両方をサポートします。 詳しくは、[パラメーターの説明](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md)の`ptmulticall`パラメーターを参照してください。 VAST形式とVMAP形式は、両方ともインストリームキューに対してサポートされています。
