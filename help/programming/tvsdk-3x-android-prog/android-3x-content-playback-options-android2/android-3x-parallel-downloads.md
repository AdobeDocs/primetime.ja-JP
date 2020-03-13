---
description: ビデオとオーディオを連続的にダウンロードするのではなく、並行的にダウンロードすると、起動時の遅延が減少します。
seo-description: ビデオとオーディオを連続的にダウンロードするのではなく、並行的にダウンロードすると、起動時の遅延が減少します。
seo-title: 並行ダウンロード
title: 並行ダウンロード
uuid: 11d37a39-391d-4127-9aa7-c94eb8a6a6a8
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 並行ダウンロード {#parallel-downloads}

ビデオとオーディオを連続的にダウンロードするのではなく、並行的にダウンロードすると、起動時の遅延が減少します。

並列ダウンロードを使用すると、ビデオオンデマンド(VOD)ファイルの再生、サーバーからの使用可能な帯域幅の最適化、バッファーの実行不足状況に陥る確率の低下、ダウンロードと再生の間の遅延を最小限に抑えることができます。

<!-- 

Removed as part of "no DASH use cases" for 2.5.1, May 31st, 2017 release.
<p>Parallel downloads allows DASH video-on-demand (VOD) files to be played, optimizes the available bandwidth usage from a server, lowers the probability of getting into buffer under-run situations, and minimizes the delay between download and playback. </p>

 -->

並行ダウンロードを行わない場合、TVSDKはビデオセグメントに対するリクエストを発行し、ビデオセグメントが読み込まれた後、1つまたは2つのオーディオセグメントをリクエストします。 並行ダウンロードでは、オーディオとビデオのセグメントが同時にダウンロードされ、連続的にはダウンロードされません。 また、セグメントごとに2つの接続と2つのHTTPリクエストが並行して行われるので、データがより高速に画面に表示されます。

>[!NOTE]
>
>この機能は、オーディオとビデオが異なるファイル（ミュクスされていないコンテンツ）にエンコードされるコンテンツにのみ適用され、MP4コンテンツ（常にミュクスされるコンテンツ）には適用されません。 HLSコンテンツは、特に代替オーディオの場合、ミュクスが解除されることがよくあります。

<!-- 

See comment above (DASH use case removed).
<note type="restriction">
  This feature applies only to content where the audio and video are encoded into different files (unmuxed content) and does not apply to MP4 content, which is always muxed. Most DASH content is unmuxed, and HLS content is often unmuxed, especially with alternate audio. 
</note>

 -->

HTTP接続では、次の段階で遅延が発生する場合があります。

* サーバーへのTCP/IP接続を確立する場合

   クライアントとサーバーは通信に同意しましたが、HTTP通信はまだ行われていません。 このタイプの遅延は、クライアントとサーバーの間のインフラストラクチャによって異なります。 このプロセスでは、クライアントとサーバーの間のインターネット経由のパスを見つけ、ルート上のすべてのデバイス（ルーターやファイアウォールなど）がデータ転送に一致することを確認する必要があります。
* TCP/IP接続を介してセグメントまたはマニフェストのHTTP要求を送信する場合。

   サーバーは要求を受け取り、処理し、クライアントへのデータの返送を開始します。 遅延の程度は、サーバー上のソフトウェアの読み込みと複雑さ、およびクライアントが要求を送信する際のアップロード接続速度によって異なります。