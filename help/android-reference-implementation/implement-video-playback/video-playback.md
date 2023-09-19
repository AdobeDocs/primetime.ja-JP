---
title: ビデオ再生の重要な操作
description: PlaybackManager は、HLS ストリーミングの重要な操作を提供します
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# ビデオ再生の重要な操作 {#essential-operations-of-video-playback}

PlaybackManager は、HLS ストリーミングの基本的な操作を提供します。

* を呼び出します。 [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)を使用することで、ビデオイベントに適切に応答できます。
* 再生、一時停止、シークなどの再生操作を提供します。
* プレーヤーのステータス、再生範囲、ビデオライブストリームなど、プレーヤーに関する情報を返します。
* ABR が有効かどうかを決定し、指定された設定データに応じて ABR およびバッファ制御パラメータを設定します。
* バッファ制御が有効かどうかを決定し、指定された構成データに応じてバッファ制御パラメータを設定します。
