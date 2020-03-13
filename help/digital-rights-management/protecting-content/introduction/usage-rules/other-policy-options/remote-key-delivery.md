---
seo-title: リモートおよびローカルのiOSキー配信
title: リモートおよびローカルのiOSキー配信
uuid: 90f672e7-9301-4e14-adca-db2a8f951a83
translation-type: tm+mt
source-git-commit: 53654b740b03c6a79394d30704a41186d4655237

---


# リモートおよびローカルのiOSキー配信 {#remote-and-local-ios-key-delivery}

Adobe Primetimeは、iOSクライアントへのキー配信に関して次のオプションをサポートしています。

* **Remote** - HTTP Live Streaming(HLS)仕様の指定に従って実行します。m3U8マニフェストは、ストリーム内の次の暗号化されたセグメントの復号化に使用するAESキーを含むHTTPSパスを指定します。 Primetime DRMポリシーで指 `Remote` 定する場合、AESキーを取得するには、クライアントデバイスがリモートのHTTPSサーバーに接続する必要があります。

* **Local**`Local` - AESキーのインターネット/ネットワークに接続する代わりにPrimetime DRMを指定すると、ローカルHTTPSサーバーがiOSアプリケーションに埋め込まれ、iOSアプリケーションですべてのAESキー要求が管理されます。 埋め込みHTTPSサーバーは、Pアプリケーションで自動的に設定され、設定されます。 アプリケーション開発者は介入を必要としません。

リモートキーの配信は、コンテンツのパッケージ化に使用されるPrimetime DRMポリシーを通じて有効になります。 この設定を変更する場合は、コンテンツを再パッケージ化する必要があります。 リモートキー配信を有効にする場合は、iOSクライアントからのキー要求を管理できるPrimetime DRMキーサーバーをデプロイする必要があります。 ただし、他のプラットフォームのクライアントのワークフローは変更されません。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>キー配信の選択は、iOSクライアントにのみ影響します。 AndroidやPrimetime on Desktop(Flash Player)など、HLSコンテンツを使用する他のすべてのデバイスは、指定されている場合でも、常に `Local` キー配信を使 `Remote` 用します。

