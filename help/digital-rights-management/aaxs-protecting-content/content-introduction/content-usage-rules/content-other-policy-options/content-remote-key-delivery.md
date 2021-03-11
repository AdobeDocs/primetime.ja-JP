---
title: リモートおよびローカルiOSキーの配信
description: リモートおよびローカルiOSキーの配信
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# リモートおよびローカルiOSキー配信{#remote-and-local-ios-key-delivery}

Adobe Primetimeは、iOSクライアントに対して主要配信を行う場合、次の2つのオプションをサポートしています。

* Remote - HLS仕様で指定されているとおり、M3U8マニフェストでは、ストリーム内の次の暗号化されたセグメントの復号化に使用するAESキーを含むHTTPSパスを指定します。 「Remote」を指定すると、クライアントデバイスはリモートのHTTPSサーバーに接続し、AESキーを取得します。
* Local - 「Local」を指定すると、AESキーをインターネットやネットワーク経由で送信する代わりに、ローカルのHTTPSサーバーがiOSアプリケーションに組み込まれ、すべてのAESキー要求を処理します。 埋め込みHTTPSサーバーは、Primetimeアプリケーションで自動的に設定および設定されます。 アプリケーション開発者は介入を必要としません。

リモートキー配信は、コンテンツのパッケージ化に使用されるポリシーによって有効になります（この設定を変更するには、コンテンツの再パッケージ化が必要です）。リモートキー配信を有効にする場合は、iOSクライアントからのキー要求を処理するAdobeアクセスキーサーバーを展開する必要があります。

>[!NOTE]
>
>「主な配信」の選択は、iOSクライアントにのみ影響します。 HLSコンテンツを使用する他のすべてのデバイスは、「Remote」が指定されている場合でも、常に「Local」キー配信を使用します。

詳しくは、「*Adobeアクセスキーサーバーの使用*」を参照してください。
