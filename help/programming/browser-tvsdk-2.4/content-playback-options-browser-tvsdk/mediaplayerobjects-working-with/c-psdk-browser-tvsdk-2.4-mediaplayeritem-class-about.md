---
description: MediaResourceが正常に読み込まれると、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-description: MediaResourceが正常に読み込まれると、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# MediaPlayerItemクラス{#about-the-mediaplayeritem-class}について

MediaResourceが正常に読み込まれると、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

`MediaResource`は、コンテンツを読み込むためにアプリケーションレイヤーが`MediaPlayer`インスタンスに発行するリクエストを表します。

`MediaPlayer`は、メディアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 `MediaPlayerItem`インスタンスは、リソースが解決された後に生成され、このインスタンスは`MediaResource`の解決されたバージョンです。 ブラウザーTVSDKは、新しく作成された`MediaPlayerItem`インスタンスに対して、`MediaPlayer.CurrentItem`を介してアクセスを提供します。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤーアイテムにアクセスする必要があります。

