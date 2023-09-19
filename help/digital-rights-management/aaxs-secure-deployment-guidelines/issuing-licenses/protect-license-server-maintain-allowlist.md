---
title: 信頼できるコンテンツパッケージ許可リストの管理
description: 信頼できるコンテンツパッケージ許可リストの管理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# 信頼できるコンテンツパッケージ許可リストの管理 {#maintain-a-allowlist-of-trusted-content-packagers}

An **許可リスト** は、信頼されているエンティティのリストです。 コンテンツパッケージャーの場合、DRM 保護されたコンテンツを作成する FLV/F4V ビデオファイルをパッケージ化（または暗号化）するために、コンテンツ所有者が信頼する組織になります。 Adobeアクセスをデプロイする場合は、信頼できるコンテンツパッケージャーの許可リストを維持し、DRM 保護ファイルの DRM メタデータ（DRM ヘッダー）に含まれるコンテンツパッケージャーの ID を確認してから、ライセンスを発行することをお勧めします。

コンテンツをパッケージ化したエンティティに関する情報の取得について詳しくは、 `V2ContentMetaData.getPackagerInfo()` （内） *Adobeアクセス API リファレンス*.
