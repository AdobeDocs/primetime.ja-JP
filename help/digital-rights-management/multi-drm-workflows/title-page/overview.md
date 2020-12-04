---
description: Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリに複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReadyおよびAdobeからのPrimetime Accessが含まれます。
seo-description: Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリに複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReadyおよびAdobeからのPrimetime Accessが含まれます。
seo-title: Multi-DRMの概要
title: Multi-DRMの概要
uuid: 1705a338-baeb-4fcd-ae16-08963da55ab8
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# Multi-DRMワークフロー{#multi-drm-workflows}

Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリに複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReadyおよびAdobeからのPrimetime Accessが含まれます。

## Multi-DRMの概要{#multi-drm-overview}

AdobeTVSDKは、複数のDRMスキームを使用したDRM保護をサポートしています。 Adobeオファー&#x200B;*Primetime DRM Cloud。ExpressPlay*&#x200B;を利用して、複数のプラットフォームでのビデオコンテンツのパッケージ化、ライセンス、再生を行います。

サポートされるDRMスキームには、Adobeの&#x200B;*Primetime Access* DRM(AAXS)、ChromeおよびAndroidの[Widevine](https://www.widevine.com)、SafariおよびiOSの[FairPlay](https://developer.apple.com/streaming/fps/)、およびa6が含まれます。>PlayReady](https://www.microsoft.com/playready/) on Edge and XboxOne. [これらのプラットフォームで現在使用可能なDRMスキームの種類や、今後のリリース予定日については、Adobeの担当者にお問い合わせください。

TVSDKは、これらのプロトコルを使用するライセンスサーバーによって発行されるDRMライセンスをサポートしています。 複数のDRMソリューションのサポートに加えて、ExpressPlayが各ソリューションのライセンスサーバーを運用するソリューションとして、Adobeオファー&#x200B;*Primetime DRM Cloud（ExpressPlay*&#x200B;を利用）がサポートされます。 これにより、DRMライセンスの発行ニーズのセットアップとメンテナンスを簡単に行うことができます。

*Primetime DRM Cloud（ExpressPlay*&#x200B;を利用）をTVSDKアプリにDRMニーズを実装するために使用するには、まず[ExpressPlay.com](https://www.expressplay.com)アカウントを取得する必要があります。 ExpressPlayは、様々なDRM保護スキームに対するライセンス機能を提供し、パッケージ化やキー管理などの他のサービスも提供します。

最初は、Adobeの担当者がExpressPlayアカウントを設定します。 その後、アカウントを設定し、ExpressPlayサーバーへのライセンストークンリクエストで使用する&#x200B;*ユーザー認証子*&#x200B;を取得します。