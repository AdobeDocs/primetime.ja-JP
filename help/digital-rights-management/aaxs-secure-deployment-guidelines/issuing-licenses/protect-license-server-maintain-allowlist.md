---
seo-title: 信頼できるコンテンツパッケージャーの許可リストの管理
title: 信頼できるコンテンツパッケージャーの許可リストの管理
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---


# 信頼できるコンテンツパッケージャーの許可リストの管理{#maintain-a-allowlist-of-trusted-content-packagers}

**許可リスト**&#x200B;は、信頼されたエンティティのリストです。 コンテンツパッケージャーの場合、組織はコンテンツ所有者からFLV/F4Vビデオファイルをパッケージ化（または暗号化）し、DRM保護されたコンテンツを作成することを信頼されます。 Adobeアクセスを展開する場合は、信頼できるコンテンツパッケージャーの許可リストを維持し、DRM保護されたファイルのDRMメタデータ（DRMヘッダー）に含まれるコンテンツパッケージャーのIDを確認してから、ライセンスを発行することをお勧めします。

コンテンツをパッケージ化したエンティティに関する情報の取得について詳しくは、『*AdobeアクセスAPIリファレンス*』の`V2ContentMetaData.getPackagerInfo()`を参照してください。
