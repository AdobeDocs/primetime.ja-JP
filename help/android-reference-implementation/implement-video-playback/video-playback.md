---
title: ビデオ再生の重要な操作
description: PlaybackManagerは、HLSストリーミングの重要な操作を提供します
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# ビデオ再生の重要な操作{#essential-operations-of-video-playback}

PlaybackManagerは、HLSストリーミングの重要な操作を提供します。

* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)を呼び出します。このリスナーは、ビデオイベントに適切に応答できます。
* 再生、一時停止、シークなどの再生操作を提供します。
* プレイヤーのステータス、再生範囲、ビデオライブストリームなど、プレイヤーに関する情報を返します。
* ABRが有効かどうかを判定し、指定した設定データに応じてABRパラメーターとバッファー制御パラメーターを設定します。
* バッファ制御が有効かどうかを判定し、指定された設定データに応じてバッファ制御パラメータを設定します。