---
title: 証明書について
description: 証明書について
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# 証明書について {#about-certificates}

Adobe Primetime DRM SDK は、次の設定で使用できます。

* Primetime DRM 実稼動 SDK
* Primetime DRM 評価 SDK
* Primetime DRM 体験版 SDK

Primetime DRM SDK を使用してライセンスサーバーを作成するには、Adobeから電子証明書を取得する必要があります。 電子証明書（単に証明書とも呼ばれます）は、個人、組織、システムなどのエンティティを特定の公開鍵と秘密鍵のペアに結び付けます。 電子証明書は、個人、システムまたは組織の ID を検証する電子資格情報と見なすことができます。

デプロイメントオプションの柔軟性とセキュリティを最大限に高めるために、Primetime DRM SDK には 4 つの証明書が必要です。

* ライセンスサーバー証明書

  SDK は、この証明書を使用して、クライアントに発行されたコンテンツライセンスに署名します。
* Packager 証明書

  SDK は、コンテンツのパッケージ化（暗号化）時に、この証明書を使用して DRM メタデータを生成します。
* トランスポート証明書

  SDK は、この証明書を使用して、クライアントとライセンスサーバー間の通信を保護します。
* ドメイン CA 証明書

  ドメインサーバーを実装するお客様には、ドメイン CA 証明書が必要です。 他の証明書とは異なり、ドメイン CA 証明書はAdobeによって発行されません。

>[!NOTE]
>
>評価用 SDK と体験版 SDK の場合、License Server、Packager、および Transport の各証明書が 1 つの証明書に結合されます。
