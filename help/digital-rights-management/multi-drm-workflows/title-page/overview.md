---
description: Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリ用の複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReady、AdobeのPrimetime Accessが含まれます。
seo-description: Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリ用の複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReady、AdobeのPrimetime Accessが含まれます。
seo-title: Multi-DRMの概要
title: Multi-DRMの概要
uuid: 1705a338-baeb-4fcd-ae16-08963da55ab8
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c

---


# Multi-DRMワークフロー {#multi-drm-workflows}

Primetime DRM Cloudを使用して、ExpressPlayを利用したTVSDKアプリ用の複数のDRMソリューションを実装できます。 DRMソリューションには、AppleのFairPlay、GoogleのWidevine、MicrosoftのPlayReady、AdobeのPrimetime Accessが含まれます。

## Multi-DRMの概要 {#multi-drm-overview}

Adobe TVSDKは、複数のDRMスキームを使用したDRM保護をサポートしています。 アドビでは、複数のプ *ラットフォームでのビデオコンテンツのパッケージ化、ライセンス、再生を行うPrimetime DRM* CloudをExpressPlayを利用して提供しています。

サポートされるDRMスキームには、Adobeの *Primetime Access* DRM(AAXS)、 [Widevine on ChromeやAndroid、](https://www.widevine.com) FairPlay [on SafariやiXBOXの](https://developer.apple.com/streaming/fps/) FairPlay [](https://www.microsoft.com/playready/) 、Xbox OS、PlayReady Edge、OneなどのネイティブDRMが含まれます。 これらのプラットフォームで現在使用可能なDRMスキームの種類や、今後のリリースの予定日については、アドビの担当者にお問い合わせください。

TVSDKは、これらのプロトコルを使用するライセンスサーバーによって発行されたDRMライセンスをサポートします。 複数のDRMソリューションのサポートに加え、アドビでは、ExpressPlayを利用した ** Primetime DRM Cloudを、ExpressPlayが各ソリューションのライセンスサーバーを運用するソリューションとして提供しています。 これにより、DRMライセンスの発行ニーズのセットアップとメンテナンスが簡単になります。

Primetime DRM CloudをExpressPlayで *利用してTVSDKアプリにDRMニーズを実装するには* 、まず [ExpressPlay.comアカウントを取得する必要があります](https://www.expressplay.com) 。 ExpressPlayは、複数の異なるDRM保護スキームのライセンス機能を提供し、パッケージ化やキー管理などの他のサービスも提供します。

アドビの担当者がExpressPlayアカウントを最初に設定します。 その後、アカウントを設定し、ExpressPlayサーバーへのライ *センストークンリクエストで* 、使用する顧客認証子を取得できます。