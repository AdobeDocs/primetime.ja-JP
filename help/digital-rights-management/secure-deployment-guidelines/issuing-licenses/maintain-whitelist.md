---
description: ホワイトリストは、信頼できるエンティティのリストです。
seo-description: ホワイトリストは、信頼できるエンティティのリストです。
seo-title: 信頼できるコンテンツパッケージャーのホワイトリストの管理
title: 信頼できるコンテンツパッケージャーのホワイトリストの管理
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 信頼できるコンテンツパッケージャーのホワイトリストの管理{#maintain-a-whitelist-of-trusted-content-packagers}

ホワイトリストは、信頼できるエンティティのリストです。

コンテンツパッケージャーの場合、エンティティは、ビデオファイルをパッケージ化（または暗号化）し、DRM保護されたコンテンツを作成するために、コンテンツ所有者に信頼される組織です。 Adobe Primetime DRMをデプロイする場合は、信頼できるコンテンツパッケージャーのホワイトリストを維持する必要があります。 また、ライセンスを発行する前に、DRM保護ファイルのDRMメタデータでコンテンツパッケージャーのIDを確認する必要があります。

コンテンツをパッケージ化したエンティティに関する情報を取得する方法については、 [V2ContentMetaData.getPackagerInfo()を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())。
