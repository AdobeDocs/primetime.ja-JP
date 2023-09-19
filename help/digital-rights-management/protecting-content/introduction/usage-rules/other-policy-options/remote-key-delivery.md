---
title: リモートおよびローカルのiOSキー配信
description: リモートおよびローカルのiOSキー配信
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# リモートおよびローカルのiOSキー配信 {#remote-and-local-ios-key-delivery}

Adobe Primetimeは、iOSクライアントへのキー配信に次のオプションをサポートしています。

* **リモート** - HTTP Live Streaming(HLS) の仕様に従って実行します。M3U8 マニフェストは、ストリーム内の次の暗号化されたセグメントを復号化するために使用する AES キーを含む HTTPS パスを指定します。 次を指定する場合： `Remote` Primetime DRM ポリシーでは、クライアントデバイスがリモート HTTPS サーバーに接続して、AES キーを取得する必要があります。

* **ローカル**  — 指定時に `Local` AES キーのインターネット/ネットワークに接続する代わりに、Primetime DRM では、ローカルの HTTPS サーバーがiOSアプリケーションに埋め込まれ、そのサーバーがすべての AES キーリクエストを管理します。 埋め込み HTTPS サーバーは、P アプリケーションで自動的に設定され、設定されます。 アプリケーション開発者が介入する必要はありません。

リモートキー配信は、コンテンツのパッケージ化に使用される Primetime DRM ポリシーを通じて有効になります。 この設定を変更する場合は、コンテンツを再パッケージ化する必要があります。 リモートキー配信を有効にする場合、iOSクライアントからのキーリクエストを管理できる Primetime DRM キーサーバーをデプロイする必要があります。 ただし、他のプラットフォームのクライアントのワークフローは変更されません。

>[!NOTE]
>
>「鍵」配信の選択は、iOSクライアントにのみ影響します。 Android や Primetime on Desktop(Flash Player) など、HLS コンテンツを使用するその他すべてのデバイスでは、常にを使用します。 `Local` キー配信 ( `Remote` が指定されています。
