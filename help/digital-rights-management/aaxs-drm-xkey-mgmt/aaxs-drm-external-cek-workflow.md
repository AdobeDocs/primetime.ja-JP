---
title: AAXS DRM外部CEKワークフロー
description: このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないため、既存のほとんどのDRMシステムとは異なります
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '178'
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
