---
description: お客様は、Adobeアクセス (AAXS)DRM を、外部 CEK 機能を備えた独自のコンテンツキー管理システム (CKMS) と共に使用できます。
title: Adobeアクセス DRM 外部 CEK の概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Adobeアクセス DRM 外部 CEK の概要 {#adobe-access-drm-external-cek-overview}

お客様は、Adobeアクセス (AAXS)DRM を、外部 CEK 機能を備えた独自のコンテンツキー管理システム (CKMS) と共に使用できます。

Adobeアクセス (AAXS)DRM では、デフォルトで、コンテンツのパッケージ化プロセス中にキー、証明書、DRM メタデータを直接処理する必要性を抽象化します。 AAXS Java SDK は、パッケージ化の際にランダムなコンテンツ暗号化キー (CEK) を自動的に生成し、それを使用してコンテンツを暗号化します。 次に、SDK は CEK 自体を暗号化し、コンテンツのメタデータに挿入します。 ライセンス発行時に、AAXS サーバは、AAXS ライセンスサーバの秘密鍵のみが必要で、CEK にメタデータからアクセスしてライセンスを生成します。
