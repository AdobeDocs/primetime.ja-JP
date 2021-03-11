---
description: お客様は、外部CEK機能を備えた独自のコンテンツキー管理システム(CKMS)でAdobeアクセス(AAXS)DRMを使用できます。
title: AdobeアクセスDRM外部CEKの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---


# AdobeアクセスDRM外部CEKの概要{#adobe-access-drm-external-cek-overview}

お客様は、外部CEK機能を備えた独自のコンテンツキー管理システム(CKMS)でAdobeアクセス(AAXS)DRMを使用できます。

Adobeアクセス(AAXS)DRMは、デフォルトで、コンテンツのパッケージ化プロセス中にキー、証明書、DRMメタデータを直接処理する必要を抽象化します。 AAXS Java SDKは、パッケージ化の際にランダムなコンテンツ暗号化キー(CEK)を自動的に生成し、それを使用してコンテンツを暗号化します。 次に、SDKがCEK自体を暗号化し、コンテンツのメタデータに挿入します。 ライセンスの発行時には、AAXSサーバーは、AAXSライセンスサーバーの秘密鍵のみを必要とし、メタデータからCEKにアクセスしてライセンスを生成します。
