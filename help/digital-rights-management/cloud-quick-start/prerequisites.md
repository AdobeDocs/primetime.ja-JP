---
title: 前提条件
description: 前提条件
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# 前提条件{#prerequisites}

コンテンツをパッケージ化する前に、Primetime DRM Packagerの証明書が必要です。 Primetime DRM証明書登録プロセスを通じて要求する必要があります。 必要なのは、Packager証明書のみです（License ServerやTransportは必要ありません）。 証明書要求の電子メールに、要求が証明書をDRMサービスで使用するものであることを示してください。

[証明書登録ガイド](../../digital-rights-management/certificate-enrollment-guide/about-certs.md)

パッケージ化証明書には、実稼働環境用と体験版の2つのレベルがあります。 体験版証明書を使用してパッケージ化されたコンテンツは開発用です。証明書の有効期限が切れた後は再生されません。 体験版コンテンツに対して発行されるすべてのライセンスには、ハードコードされたポリシーの最大有効期限が、証明書の有効期限と同じ（DRMポリシーで設定されていない場合）になります。
