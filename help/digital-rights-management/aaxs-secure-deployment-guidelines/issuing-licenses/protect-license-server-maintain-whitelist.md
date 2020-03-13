---
seo-title: 信頼できるコンテンツパッケージャーのホワイトリストの管理
title: 信頼できるコンテンツパッケージャーのホワイトリストの管理
uuid: ad40993c-15c3-43b2-9593-7b75802cfe69
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 信頼できるコンテンツパッケージャーのホワイトリストの管理{#maintain-a-whitelist-of-trusted-content-packagers}

ホワイ *トリスト* は信頼できるエンティティのリストです。 コンテンツパッケージャーの場合、DRM保護されたコンテンツを作成する際に、FLV/F4Vビデオファイルをパッケージ化（または暗号化）することをコンテンツ所有者が信頼している組織です。 Adobe Accessをデプロイする場合は、信頼できるコンテンツパッケージャーのホワイトリストを維持し、ライセンスを発行する前に、DRM保護ファイルのDRMメタデータ（DRMヘッダー）に含まれるコンテンツパッケージャーのIDを確認することをお勧めします。

コンテンツをパッケージ化したエンティティに関する情報の取得について詳しくは、『 `V2ContentMetaData.getPackagerInfo()` Adobe Access APIリファレンス』のを参照してください **。
