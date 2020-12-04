---
description: このガイドは、Javaに実装されているAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。
seo-description: このガイドは、Javaに実装されているAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。
seo-title: 製品の概要、オーディエンス、および本ガイド
title: 製品の概要、オーディエンス、および本ガイド
uuid: 638bafbe-e518-4891-b792-29f765c3c0d7
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---


# 製品の概要、オーディエンス、および本ガイド{#product-overview-audience-and-this-guide}

このガイドは、Javaに実装されているAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。

<!--<a id="section_FC24E86A2E6442B8A3769160769BBDFA"></a>-->

* TVSDKがサポートする機能のリストについては、[Primetime TVSDKの機能](../../tvsdk-2.7-for-android/overview-prod-audience-guide/c-psdk-android-2.7-overview-of-the-player.md)を参照してください。
* TVSDKを使用するための特定のハードウェアおよびソフトウェアの要件については、[要件](../../tvsdk-2.7-for-android/c-psdk-android-2.7-requirements.md)を参照してください。
* 使用可能なAPIのリストについては、[TVSDK Android APIs](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/)を参照してください。

## 製品概要{#section_9664959F25C948878F2F7EF3D360CA95}

TVSDKには、高度なビデオ機能、コンテンツ保護、広告機能をプレイヤーに組み込むのに役立つ、APIの説明とコードサンプルが含まれています。 Javaを使用して、ビデオプレーヤーのユーザーインターフェイスを作成します。 TVSDKは、そのユーザーインターフェイスをメディアプレイヤーに接続するのに役立ちます。 これにより、メディアのマニフェストに基づいてビデオや広告を再生できます。 また、TVSDKを使用して、ビデオに関する情報の取得、セキュリティの処理、再生の制御および監視を行うこともできます。

## オーディエンス{#section_527860B373734D3BA89FCF5EC1F6DC37}

このガイドは、読者がJavaを使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 JavaでビデオプレイヤUIを実装し、必要なTVSDK機能を組み込みます。

## このガイドについて{#section_9A5B2FC506B34B5DB71CA827B307A4D0}

このガイドでは、AndroidデバイスでJavaを使用するビデオプレイヤーにTVSDK機能を組み込むことができる情報を提供します。

## このガイドの名前空間表記{#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>TVSDK API名前空間プレフィックス[!DNL com.adobe.mediacore]は、簡潔にするために省略されることがよくあります。
>
>コンテキストが明確な場合、多くのAPIエレメントは、親クラス指定子なしで参照されます。