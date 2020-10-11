---
title: VODにAd Insertionを使用
description: VODにAd Insertionを使用する
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# VODにAd Insertionを使用 {#ad-insertion-vod}

PrimetimeAd Insertionは、標準のVAST 3.0以降またはVMAP 1.0以降の形式を使用して、複数のVODアセットへの広告挿入をサポートします。

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD（サーバーマップ広告） {#server-mapped-ads}

PrimetimeAd Insertionでは、VMAP形式で定義された広告タイムライン情報を使用して、再生開始前に広告を挿入するVOD挿入をサポートしています。  breakStart/breakEndビーコンなどのVMAP固有の広告トラッキングは、 [広告トラッキングと共に提供されます](set-up-ad-tracking.md)。

## フルイベント再生(Ad Decisioningキューを含むVOD) {#full-event-replay}

PrimetimeAd Insertionは、以前に記録されたライブイベントの再生時など、コンテンツストリーム自体のキューを含む特殊なVODアセットもサポートします。 サポートする広告決定キュー（またはキュー形式）のタイプについて詳しくは、「ライブ/リニアでの [Ad Insertionの使用](ad-insertion-live-linear-stream.md)」を参照してください。

複数の広告ブレークを含むVODアセットに対して、単一の広告リクエストシナリオと並行する複数の広告リクエストシナリオの両方をサポートします。 詳しくは、パラメーターの説明の「 `ptmulticall` パラメーター」を参照して [ください](/help/dynamic-ad-insertion/msapi-topics/ms-getting-started/ms-api-query-params.md)。 VAST形式とVMAP形式は、両方ともインストリームキューに対してサポートされています。
