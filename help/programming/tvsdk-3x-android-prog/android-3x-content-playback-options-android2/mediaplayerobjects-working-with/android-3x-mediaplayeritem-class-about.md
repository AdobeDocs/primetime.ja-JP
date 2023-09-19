---
description: MediaResource オブジェクトの読み込みが完了すると、 TVSDK は MediaPlayerItem クラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
title: MediaPlayerItem クラスについて
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# MediaPlayerItem クラスについて {#about-the-mediaplayeritem-class}

MediaPlayer オブジェクトは、使用するメディアプレーヤーを表します。 MediaPlayerItem は、プレーヤー上のオーディオまたはビデオを表します。

MediaResource オブジェクトの読み込みが完了すると、 TVSDK は MediaPlayerItem クラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

The `MediaResource` は、アプリケーションレイヤーによって `MediaPlayer` インスタンスを使用して、コンテンツを読み込みます。

The `MediaPlayer` メディアリソースを解決し、関連するマニフェストファイルを読み込んで、マニフェストを解析します。 これは、リソースの読み込みプロセスの非同期部分です。 The `MediaPlayerItem` インスタンスは、リソースが解決された後に生成され、このインスタンスは、 `MediaResource`. TVSDK は、新しく作成された `MediaPlayerItem` インスタンス経由で `MediaPlayer.CurrentItem`.

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレーヤーアイテムにアクセスする必要があります。
