---
description: ビデオとオーディオを一連ではなく並行してダウンロードすることで、起動時の遅延が軽減されます。
title: 並列ダウンロード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 並列ダウンロード {#parallel-downloads}

ビデオとオーディオを一連ではなく並行してダウンロードすることで、起動時の遅延が軽減されます。

並列ダウンロードを使用すると、ビデオオンデマンド (VOD) ファイルを再生でき、サーバーからの使用可能な帯域幅の使用を最適化し、バッファーが実行中の状況に陥る確率を下げ、ダウンロードと再生の間の遅延を最小限に抑えます。

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

並列ダウンロードを行わない場合、 TVSDK はビデオセグメントに対するリクエストを発行し、ビデオセグメントの読み込み後に、1 つまたは 2 つのオーディオセグメントをリクエストします。 並列ダウンロードでは、オーディオおよびビデオセグメントが同時にダウンロードされ、順番にはダウンロードされません。 また、同時に 2 つの接続と 1 つのセグメントにつき 2 つの HTTP リクエストがあるので、データが画面に表示される時間が短くなります。

>[!NOTE]
>
>この機能は、オーディオとビデオが異なるファイル（無修正コンテンツ）にエンコードされるコンテンツにのみ適用され、MP4 コンテンツ（常に無修正コンテンツ）には適用されません。 HLS コンテンツは、多くの場合、ミュークス化解除されます。特に代替オーディオではミュート解除されます。

<!-- 

See comment above (DASH use case removed).
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
-->

HTTP 接続では、次の段階で遅延が発生する場合があります。

* サーバーへの TCP/IP 接続を確立する場合

  クライアントとサーバーは通信に同意しましたが、HTTP 通信はまだ行われていません。 このタイプの遅延は、クライアントとサーバーの間のインフラストラクチャによって異なります。 このプロセスでは、クライアントとサーバーの間のインターネット経由のパスを見つけ、ルーターやファイアウォールなど、ルート上のすべてのデバイスがデータ転送に同意していることを確認する必要があります。
* TCP/IP 接続を介してセグメントまたはマニフェストの HTTP リクエストを送信する場合。

  サーバーが要求を受け取り、処理して、データのクライアントへの送信を開始します。 遅延の程度は、サーバー上のソフトウェアの負荷と複雑さ、およびクライアントが要求を送信した際のアップロード接続速度によって異なります。
