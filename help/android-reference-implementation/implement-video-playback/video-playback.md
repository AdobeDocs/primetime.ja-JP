---
seo-title: ビデオ再生の重要な操作
title: ビデオ再生の重要な操作
description: PlaybackManagerは、HLSストリーミングの重要な操作を提供します
seo-description: PlaybackManagerは、HLSストリーミングの重要な操作を提供します
uuid: 7ac93f1f-9233-4462-a4be-528d1aa524a9
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# ビデオ再生の重要な操作{#essential-operations-of-video-playback}

PlaybackManagerは、HLSストリーミングの重要な操作を提供します。

* [PlaybackManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/PlaybackManager.PlaybackManagerEventListener.html)を呼び出します。このリスナーは、ビデオイベントに適切に応答できます。
* 再生、一時停止、シークなどの再生操作を提供します。
* プレイヤーのステータス、再生範囲、ビデオライブストリームなど、プレイヤーに関する情報を返します。
* ABRが有効かどうかを判定し、指定した設定データに応じてABRパラメーターとバッファー制御パラメーターを設定します。
* バッファ制御が有効かどうかを判定し、指定された設定データに応じてバッファ制御パラメータを設定します。