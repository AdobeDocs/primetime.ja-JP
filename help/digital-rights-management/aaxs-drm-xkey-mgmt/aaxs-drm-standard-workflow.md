---
seo-title: 標準AAXS DRMワークフロー
title: 標準AAXS DRMワークフロー
description: 標準AAXS DRMワークフロー
seo-description: 標準AAXS DRMワークフロー
uuid: b996eb2c-8e37-4a29-a972-e09c69d2461d
translation-type: tm+mt
source-git-commit: 17a492d30c65b1b5e12419f04afa0116654b99fc

---


# 標準AAXS DRMワークフロー{#standard-aaxs-drm-workflow}

1. （パッケージ）AAXS Java SDKがランダムなCEKを生成します。
1. （パッケージ）CEKはコンテンツの暗号化に使用されます。
1. （パッケージ）CEKは、AAXSライセンスサーバーの公開鍵を使用して暗号化されます。
1. （パッケージ）暗号化されたCEKがコンテンツのDRMメタデータに挿入されます。
1. デバイスは、AAXSサーバーからライセンスを要求して、コンテンツの再生を試みます。
1. （ライセンス）AAXSサーバーは、その秘密鍵を使用して、メタデータからCEKを復号化します。
1. （ライセンス）AAXSサーバーは、CEKを含むライセンスをデバイスに発行します。
