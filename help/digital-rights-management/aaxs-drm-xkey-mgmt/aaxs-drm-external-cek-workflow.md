---
seo-title: AAXS DRM外部CEKワークフロー
title: AAXS DRM外部CEKワークフロー
description: このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないので、既存のほとんどのDRMシステムとは別のものです。
seo-description: このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないので、既存のほとんどのDRMシステムとは別のものです。
uuid: b313594b-0feb-4f27-bf02-f04b955e2140
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

---


# AAXS DRM外部CEKワークフロー{#aaxs-drm-external-cek-workflow}

このワークフローは、中央リポジトリやコンテンツキー管理システム(CKMS)を使用する必要がないので、既存のほとんどのDRMシステムとは異なります。 ただし、AAXSで既存のCKMSを使用したいお客様の場合、AAXSには「外部CEK」と呼ばれる機能が用意されており、パッケージ化とライセンス発行時にCEKが外部から提供されます。

![](assets/ECEK_Workflow.PNG)

1. （パッケージ）AAXS Java SDKは、CEKとCEK IDを備えています。
1. （パッケージ）CEKはコンテンツの暗号化に使用されます。
1. （パッケージ）CEK IDがコンテンツのDRMメタデータに挿入されます。
1. デバイスは、AAXSサーバーからライセンスを要求して、コンテンツの再生を試みます。
1. （ライセンス）AAXSサーバーは、コンテンツのメタデータからCEK IDを抽出します。
1. AAXSサーバーは、CKMSからCEKを取得します。
1. （ライセンス）AAXSサーバーは、CEKを含むライセンスをデバイスに発行します。
