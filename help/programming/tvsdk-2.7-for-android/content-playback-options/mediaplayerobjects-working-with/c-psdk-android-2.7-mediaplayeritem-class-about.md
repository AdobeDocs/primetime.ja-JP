---
description: MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-description: MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: 2d37f358-d158-481b-81d5-27546e9c2e0e
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# MediaPlayerItemクラス{#about-the-mediaplayeritem-class}について

MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。

MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

`MediaResource`は、コンテンツを読み込むためにアプリケーションレイヤーが`MediaPlayer`インスタンスに発行するリクエストを表します。

`MediaPlayer`は、メディアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 `MediaPlayerItem`インスタンスは、リソースが解決された後に生成され、このインスタンスは`MediaResource`の解決されたバージョンです。 TVSDKは、新しく作成された`MediaPlayerItem`インスタンスに対して、`MediaPlayer.CurrentItem`を介してアクセスを提供します。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤーアイテムにアクセスする必要があります。