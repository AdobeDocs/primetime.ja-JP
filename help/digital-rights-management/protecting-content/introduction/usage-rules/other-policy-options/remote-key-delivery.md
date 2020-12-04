---
seo-title: リモートおよびローカルのiOSキー配信
title: リモートおよびローカルのiOSキー配信
uuid: 90f672e7-9301-4e14-adca-db2a8f951a83
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# リモートおよびローカルのiOSキー配信{#remote-and-local-ios-key-delivery}

Adobe Primetimeは、iOSクライアントに対して主要配信の次のオプションをサポートしています。

* **Remote**  - HTTP Live Streaming(HLS)仕様の指定に従って実行します。M3U8マニフェストは、ストリーム内の次の暗号化されたセグメントの復号化に使用する必要があるAESキーを含むHTTPSパスを指定します。Primetime DRMポリシーで`Remote`を指定する場合、クライアントデバイスはリモートのHTTPSサーバーに接続してAESキーを取得する必要があります。

* **ローカル** - AESキー `Local` のインターネット/ネットワークに接続する代わりにPrimetime DRMで指定する場合、ローカルHTTPSサーバーがiOSアプリケーションに埋め込まれ、iOSアプリケーションですべてのAESキーリクエストが管理されます。埋め込みHTTPSサーバーは、Pアプリケーションで自動的に設定および設定されます。 アプリケーション開発者は介入を必要としません。

リモートキー配信は、コンテンツのパッケージ化に使用されるPrimetime DRMポリシーによって有効になります。 この設定を変更する場合は、コンテンツを再パッケージ化する必要があります。 リモートキーの配信を有効にする場合、iOSクライアントからのキー要求を管理できるPrimetime DRMキーサーバーを展開する必要があります。 ただし、他のプラットフォームのクライアントのワークフローに変更はありません。

>[!NOTE]
>
>「主な配信」の選択は、iOSクライアントにのみ影響します。 AndroidやPrimetime on Desktop(Flash Player)など、HLSコンテンツを使用する他のすべてのデバイスは、`Remote`が指定されている場合でも、常に`Local`キー配信を使用します。

