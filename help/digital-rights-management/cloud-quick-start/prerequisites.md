---
title: 前提条件
description: 前提条件
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# 前提条件 {#prerequisites}

コンテンツをパッケージ化する前に、Primetime DRM Packager 証明書が必要です。 Primetime DRM 証明書登録プロセスを通じて要求する必要があります。 パッケージャ証明書のみが必要です（ライセンスサーバーやトランスポートは不要）。 証明書の要求の電子メールに、DRM サービスで使用する証明書を要求する旨を記載してください。

[証明書登録ガイド](../../digital-rights-management/certificate-enrollment-guide/about-certs.md)

パッケージ化証明書には、PRODUCTION と TRIAL の 2 つのレベルがあります。 TRIAL 証明書を使用してパッケージ化されたコンテンツは、開発でのみ使用され、証明書の有効期限が切れた後は再生されません。 体験版コンテンツに対して発行されるすべてのライセンスには、証明書の有効期限と同じ、ハードコードされたポリシーの最大有効期限が設定されます（DRM ポリシーに設定されていない場合）。
