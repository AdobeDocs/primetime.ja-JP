---
description: 許可リストとは、信頼されたエンティティのリストです。
seo-description: 許可リストとは、信頼されたエンティティのリストです。
seo-title: 信頼できるコンテンツパッケージャーの許可リストの管理
title: 信頼できるコンテンツパッケージャーの許可リストの管理
uuid: 9a132ef9-eb56-408a-939e-1acd32d83a33
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# 信頼できるコンテンツパッケージャーの許可リストの管理{#maintain-a-allowlist-of-trusted-content-packagers}

許可リストとは、信頼されたエンティティのリストです。

コンテンツパッケージャーの場合、エンティティは、コンテンツ所有者に信頼されて、ビデオファイルのパッケージ化（または暗号化）やDRM保護コンテンツの作成を行う組織です。 Adobe PrimetimeDRMを展開する場合は、信頼できるコンテンツパッケージャーの許可リストを維持する必要があります。 また、ライセンスを発行する前に、DRM保護ファイルのDRMメタデータ内のコンテンツパッケージャーのIDを検証する必要があります。

コンテンツをパッケージ化したエンティティに関する情報を取得する方法については、[V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())を参照してください。
