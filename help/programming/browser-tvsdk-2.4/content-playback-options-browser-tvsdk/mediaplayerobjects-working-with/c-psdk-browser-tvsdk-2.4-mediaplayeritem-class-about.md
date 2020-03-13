---
description: MediaResourceが正常に読み込まれた後、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-description: MediaResourceが正常に読み込まれた後、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: 5226d3ad-2438-44fe-a8ef-bcc0da8331b8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayerItemクラスについて{#about-the-mediaplayeritem-class}

MediaResourceが正常に読み込まれた後、Browser TVSDKは、MediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

は、コ `MediaResource` ンテンツを読み込むためにアプリケーションレイヤーがインスタンスに対して発行 `MediaPlayer` するリクエストを表します。

は、メデ `MediaPlayer` ィアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 このイ `MediaPlayerItem``MediaResource`ンスタンスは、リソースが解決された後に生成され、このインスタンスは、解決されたバージョンの ブラウザーTVSDKは、を通じて新しく作成されたインスタンスへのア `MediaPlayerItem` クセスを提供しま `MediaPlayer.CurrentItem`す。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤー項目にアクセスする必要があります。

