---
title: VOD にAd Insertionを使用
description: VOD にAd Insertionを使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# VOD にAd Insertionを使用 {#ad-insertion-vod}

PrimetimeAd Insertionは、標準の VAST 3.0 以降または VMAP 1.0 以降の形式を使用して、複数の VOD アセットへの広告挿入をサポートします。

* [IAB VMAP](https://www.iab.com/wp-content/uploads/2015/06/VMAPv1_0.pdf)

* [IAB VAST](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf)

## VOD（広告マップ） {#server-mapped-ads}

PrimetimeAd Insertionは、VMAP 形式で定義された広告タイムライン情報を使用して、再生開始前に広告が挿入された VOD 挿入をサポートします。  breakStart/breakEnd ビーコンなどの VMAP 固有の広告トラッキングは、 [広告トラッキング](set-up-ad-tracking.md).

## フルイベント再生 (VOD とAd Decisioningキュー ) {#full-event-replay}

また、PrimetimeAd Insertionは、以前に記録されたライブイベントの再生など、コンテンツストリーム自体のキューを含む特殊な VOD アセットもサポートしています。 サポートする広告の判定キュー（またはキュー形式）のタイプについて詳しくは、 [ライブ/リニアでのAd Insertionの使用](ad-insertion-live-linear-stream.md).

複数の広告ブレークを含む VOD アセットでは、単一の広告リクエストと並行する複数の広告リクエストのシナリオを両方ともサポートしています。 詳しくは、 `ptmulticall` のパラメーター [パラメーターの説明](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md). VAST および VMAP 形式は、両方とも、インストリームキューでサポートされています。
