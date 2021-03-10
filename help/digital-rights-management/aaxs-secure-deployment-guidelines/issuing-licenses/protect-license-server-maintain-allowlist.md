---
title: 信頼できるコンテンツパッケージャーの許可リストの管理
description: 信頼できるコンテンツパッケージャーの許可リストの管理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# 信頼できるコンテンツパッケージャーの許可リストの管理{#maintain-a-allowlist-of-trusted-content-packagers}

**許可リスト**&#x200B;は、信頼されたエンティティのリストです。 コンテンツパッケージャーの場合、組織はコンテンツ所有者からFLV/F4Vビデオファイルをパッケージ化（または暗号化）し、DRM保護されたコンテンツを作成することを信頼されます。 Adobeアクセスを展開する場合は、信頼できるコンテンツパッケージャーの許可リストを維持し、DRM保護されたファイルのDRMメタデータ（DRMヘッダー）に含まれるコンテンツパッケージャーのIDを確認してから、ライセンスを発行することをお勧めします。

コンテンツをパッケージ化したエンティティに関する情報の取得について詳しくは、『*AdobeアクセスAPIリファレンス*』の`V2ContentMetaData.getPackagerInfo()`を参照してください。
