---
title: 標準 AAXS DRM ワークフロー
description: 標準 AAXS DRM ワークフロー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# 標準 AAXS DRM ワークフロー{#standard-aaxs-drm-workflow}

1. （パッケージ）AAXS Java SDK は、ランダムな CEK を生成します。
1. （パッケージ）CEK はコンテンツの暗号化に使用されます。
1. （パッケージ）CEK は、AAXS License Server の公開鍵を使用して暗号化されます。
1. （パッケージ）暗号化された CEK がコンテンツの DRM メタデータに挿入されます。
1. デバイスは、AAXS サーバーからライセンスを要求して、コンテンツを再生しようとします。
1. （ライセンス）AAXS サーバーは、秘密鍵を使用して、メタデータから CEK を復号化します。
1. （ライセンス）AAXS サーバーは、CEK を含むライセンスをデバイスに発行します。
