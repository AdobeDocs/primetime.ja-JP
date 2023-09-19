---
title: AAXS DRM 外部 CEK ワークフロー
description: このワークフローは、中央リポジトリや CKMS(Content Key Management System) を使用する必要がないので、既存のほとんどの DRM システムからの出発点となります。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# AAXS DRM 外部 CEK ワークフロー{#aaxs-drm-external-cek-workflow}

このワークフローは、中央リポジトリや CKMS(Content Key Management System) を使用する必要がないので、既存のほとんどの DRM システムからの出発点となります。 ただし、AAXS が既存の CKMS と連携することを望むお客様に対しては、AAXS は「外部 CEK」と呼ばれる機能を提供し、パッケージ化およびライセンス発行時に CEK が外部から提供されます。

![](assets/ECEK_Workflow.PNG)

1. （パッケージ）AAXS Java SDK は、CEK と CEK ID を備えています。
1. （パッケージ）CEK はコンテンツの暗号化に使用されます。
1. （パッケージ）CEK ID がコンテンツの DRM メタデータに挿入されます。
1. デバイスは、AAXS サーバーからライセンスを要求して、コンテンツを再生しようとします。
1. （ライセンス）AAXS サーバーは、コンテンツメタデータから CEK ID を抽出します。
1. AAXS サーバーは、CKMS から CEK を取得します。
1. （ライセンス）AAXS サーバーは、CEK を含むライセンスをデバイスに発行します。
