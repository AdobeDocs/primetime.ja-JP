---
seo-title: 信頼できるコンテンツパッケージャーの許可リストの管理
title: 信頼できるコンテンツパッケージャーの許可リストの管理
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# 信頼できるコンテンツパッケージャーの許可リストの管理{#maintain-a-allowlist-of-trusted-content-packagers}

*許可リスト* は、信頼されたエンティティのリストです。 コンテンツパッケージャーの場合、組織はコンテンツ所有者からFLV/F4Vビデオファイルをパッケージ化（または暗号化）し、DRM保護されたコンテンツを作成することを信頼されます。 Adobe Accessをデプロイする場合は、信頼できるコンテンツパッケージャーの許可リストを維持し、DRM保護されたファイルのDRMメタデータ（DRMヘッダー）に含まれるコンテンツパッケージャーのIDを確認してから、ライセンスを発行することをお勧めします。

コンテンツをパッケージ化したエンティティに関する情報の取得について詳しくは、『 `V2ContentMetaData.getPackagerInfo()` Adobe Access API Reference **』の「」を参照してください。
