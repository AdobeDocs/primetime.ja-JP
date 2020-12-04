---
seo-title: AAXS DRM外部CEKワークフロー
title: AAXS DRM外部CEKワークフロー
description: このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないため、既存のほとんどのDRMシステムとは異なります
seo-description: このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないため、既存のほとんどのDRMシステムとは異なります
uuid: b313594b-0feb-4f27-bf02-f04b955e2140
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# AAXS DRM外部CEKワークフロー{#aaxs-drm-external-cek-workflow}

このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないため、既存のほとんどのDRMシステムとは異なります。 ただし、AAXSで既存のCKMSを使用したいお客様の場合、AAXSには「External CEK」と呼ばれる機能があり、パッケージ化とライセンス発行時にCEKが外部から提供されます。

![](assets/ECEK_Workflow.PNG)

1. （パッケージ）AAXS Java SDKは、CEKとCEK IDを備えています。
1. （パッケージ）CEKは、コンテンツの暗号化に使用されます。
1. （パッケージ）CEK IDがコンテンツのDRMメタデータに挿入されます。
1. デバイスは、AAXSサーバーにライセンスを要求してコンテンツを再生しようとします。
1. （ライセンス認証）AAXSサーバーは、コンテンツメタデータからCEK IDを抽出します。
1. AAXSサーバーはCKMSからCEKを取得します。
1. （ライセンス認証）AAXSサーバーは、CEKを含むライセンスをデバイスに発行します。
