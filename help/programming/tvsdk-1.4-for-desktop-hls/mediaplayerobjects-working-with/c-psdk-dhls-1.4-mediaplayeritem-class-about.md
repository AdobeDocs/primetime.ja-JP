---
description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-description: MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: 531dd1a6-d72c-4ae3-9c3f-2f1d854245c5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# MediaPlayerItemクラスについて{#about-the-mediaplayeritem-class}

MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。

<!--<a id="section_01BC89E5C5A94D0A95EF9D29FBCE758A"></a>-->

メディアリソースが正常に読み込まれた後、TVSDKは、そのリソースへのアクセスを提供する `MediaPlayerItem` クラスのインスタンスを作成します。

は、コ `MediaResource` ンテンツを読み込むためにアプリケーションレイヤーがインスタンスに対して発行 `MediaPlayer` するリクエストを表します。

は、メデ `MediaPlayer` ィアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 このイ `MediaPlayerItem``MediaResource`ンスタンスは、リソースが解決された後に生成され、このインスタンスは、解決されたバージョンの TVSDKは、を通じて新しく作成されたインスタンスへのアクセス `MediaPlayerItem` を提供しま `MediaPlayer.currentItem`す。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤー項目にアクセスする必要があります。

