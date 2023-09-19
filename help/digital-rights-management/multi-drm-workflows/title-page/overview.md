---
description: ExpressPlay を活用した Primetime DRM Cloud を使用して、TVSDK アプリに複数の DRM ソリューションを実装できます。 DRM ソリューションには、Appleの FairPlay、Googleの Widevine、Microsoftの PlayReady、Adobeからの Primetime Access などがあります。
title: Multi-DRM の概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Multi-DRM ワークフロー {#multi-drm-workflows}

ExpressPlay を活用した Primetime DRM Cloud を使用して、TVSDK アプリに複数の DRM ソリューションを実装できます。 DRM ソリューションには、Appleの FairPlay、Googleの Widevine、Microsoftの PlayReady、Adobeからの Primetime Access などがあります。

## Multi-DRM の概要 {#multi-drm-overview}

AdobeTVSDK は、複数の DRM スキームを使用した DRM 保護をサポートしています。 Adobeオファー *Primetime DRM Cloud（ExpressPlay を利用）* 複数のプラットフォームでのビデオコンテンツのパッケージ化、ライセンス、再生を提供する。

サポートされる DRM スキームにはAdobeの *Primetime アクセス* DRM(AAXS) と、を含む様々なデバイス上のネイティブ DRM [Widevine](https://www.widevine.com) （Chrome および Android の場合） [FairPlay](https://developer.apple.com/streaming/fps/) (Safari とiOS、および [PlayReady](https://www.microsoft.com/playready/) Edge と XboxOne で これらのAdobeで現在利用可能な DRM スキームの種類や、今後のリリース予定日については、プラットフォーム担当者にお問い合わせください。

TVSDK は、これらのプロトコルを使用する任意のライセンスサーバーによって発行された DRM ライセンスをサポートします。 複数の DRM ソリューションのサポートに加えて、Adobeオファー *Primetime DRM Cloud（ExpressPlay を利用）* ExpressPlay が各ソリューションのライセンスサーバを運用するソリューションとして。 これにより、DRM ライセンスの発行ニーズに合わせたセットアップとメンテナンスを簡素化できます。

次を使用するには： *Primetime DRM Cloud（ExpressPlay を利用）* TVSDK アプリで DRM のニーズを実装するには、まず [ExpressPlay.com](https://www.expressplay.com) アカウント。 ExpressPlay は、さまざまな DRM 保護スキームに対するライセンス機能を提供し、パッケージ化や鍵管理などの他のサービスも提供します。

Adobeの担当者が最初に ExpressPlay アカウントを設定します。 その後、アカウントを設定し、 *顧客認証子* ExpressPlay サーバーへのライセンストークンリクエストで使用する
