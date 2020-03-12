---
description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: d7f65edf-4693-4b1e-bae0-46fadce98751
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerItemクラスについて{#about-the-mediaplayeritem-class}

MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。

メディアリソースが正常に読み込まれた後、TVSDKは、そのリソースへのアクセスを提供する `MediaPlayerItem` クラスのインスタンスを作成します。

は、コ `MediaResource` ンテンツを読み込むためにアプリケーションレイヤーがインスタンスに対して発行 `MediaPlayer` するリクエストを表します。

は、メデ `MediaPlayer` ィアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 このイ `MediaPlayerItem``MediaResource`ンスタンスは、リソースが解決された後に生成され、このインスタンスは、解決されたバージョンの TVSDKは、新しく作成されたインスタンスに対し、 `MediaPlayerItem``MediaPlayer.CurrentItem`

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤー項目にアクセスする必要があります。

