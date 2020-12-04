---
description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: d7f65edf-4693-4b1e-bae0-46fadce98751
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---


# MediaPlayerItemクラス{#about-the-mediaplayeritem-class}について

MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。

メディアリソースが正常に読み込まれた後、TVSDKは`MediaPlayerItem`クラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

`MediaResource`は、コンテンツを読み込むためにアプリケーションレイヤーが`MediaPlayer`インスタンスに発行するリクエストを表します。

`MediaPlayer`は、メディアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 `MediaPlayerItem`インスタンスは、リソースが解決された後に生成され、このインスタンスは`MediaResource`の解決されたバージョンです。 TVSDKは、新しく作成された`MediaPlayerItem`インスタンスに対して、`MediaPlayer.CurrentItem`を介してアクセスを提供します

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤーアイテムにアクセスする必要があります。

