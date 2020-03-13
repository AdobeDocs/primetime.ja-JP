---
description: MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-description: MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。
seo-title: MediaPlayerItemクラスについて
title: MediaPlayerItemクラスについて
uuid: fc79c442-2e38-48c4-8ef9-6dce9ad6790a
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# MediaPlayerItemクラスについて {#about-the-mediaplayeritem-class}

MediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 MediaPlayerItemは、プレーヤー上のオーディオまたはビデオを表します。

MediaResourceオブジェクトの読み込みが完了すると、TVSDKはMediaPlayerItemクラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

は、コ `MediaResource` ンテンツを読み込むためにアプリケーションレイヤーがインスタンスに対して発行 `MediaPlayer` するリクエストを表します。

は、メデ `MediaPlayer` ィアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 このイ `MediaPlayerItem``MediaResource`ンスタンスは、リソースが解決された後に生成され、このインスタンスは、解決されたバージョンの TVSDKは、を通じて新しく作成されたインスタンスへのアクセス `MediaPlayerItem` を提供しま `MediaPlayer.CurrentItem`す。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤー項目にアクセスする必要があります。