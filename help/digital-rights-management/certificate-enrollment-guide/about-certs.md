---
title: 証明書について
description: 証明書について
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 証明書について{#about-certificates}

Adobe PrimetimeDRM SDKは、次の設定で利用できます。

* Primetime DRM実稼働SDK
* Primetime DRM評価SDK
* Primetime DRM体験版SDK

Primetime DRM SDKを使用してライセンスサーバーを作成するには、Adobeからデジタル証明書を取得する必要があります。 デジタル証明書（単に証明書とも呼ばれる）は、個人、組織、システムなどのエンティティを特定の公開鍵と秘密鍵のペアに連結します。 デジタル証明書は、個人、システムまたは組織のIDを検証する電子証明書と見なすことができます。

デプロイメントオプションで最大限の柔軟性とセキュリティ強化を実現するために、Primetime DRM SDKには4つの証明書が必要です。

* ライセンスサーバー証明書

   SDKは、この証明書を使用して、クライアントに発行されたコンテンツライセンスに署名します。
* Packager証明書

   SDKは、コンテンツをパッケージ化（暗号化）する際に、この証明書を使用してDRMメタデータを生成します。
* トランスポート証明書

   SDKは、この証明書を使用して、クライアントとライセンスサーバー間の通信を保護します。
* ドメインCA証明書

   ドメインサーバーを実装する場合は、ドメインCA証明書が必要です。 他の証明書とは異なり、ドメインCA証明書はAdobeから発行されません。

>[!NOTE]
>
>評価版SDKと体験版SDKの場合、ライセンスサーバー、Packager、トランスポートの各証明書が1つの証明書に結合されます。

