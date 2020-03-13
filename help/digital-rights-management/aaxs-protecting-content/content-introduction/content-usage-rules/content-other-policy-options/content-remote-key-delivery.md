---
seo-title: リモートおよびローカルのiOSキー配信
title: リモートおよびローカルのiOSキー配信
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# リモートおよびローカルのiOSキー配信{#remote-and-local-ios-key-delivery}

Adobe Primetimeは、iOSクライアントへのキー配信に関して、次の2つのオプションをサポートしています。

* Remote - HLS仕様で指定されたとおり、M3U8マニフェストは、ストリーム内の次の暗号化されたセグメントの復号化に使用するAESキーを含むHTTPSパスを指定します。 「Remote」を指定すると、クライアントデバイスはリモートのHTTPSサーバーに接続し、AESキーを取得します。
* Local - 「Local」を指定した場合、AESキーのインターネットやネットワーク経由で送信する代わりに、ローカルHTTPSサーバーがiOSアプリケーションに組み込まれ、すべてのAESキー要求を処理します。 埋め込みHTTPSサーバーは、Primetimeアプリケーションで自動的に設定および設定されます。 アプリケーション開発者は介入を必要としません。

リモートキー配信は、コンテンツのパッケージ化に使用されるポリシーを通じて有効になります（この設定を変更するには、コンテンツの再パッケージ化が必要です）。リモートキー配信を有効にする場合は、iOSクライアントからのキー要求を処理するAdobe Access Key Serverを展開する必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>キー配信の選択は、iOSクライアントにのみ影響します。 HLSコンテンツを使用する他のすべてのデバイスは、「Remote」が指定されていても、常に「ローカル」キー配信を使用します。

詳しくは、「Adobe Accessキー *サーバーの使用」を参照してください*。
