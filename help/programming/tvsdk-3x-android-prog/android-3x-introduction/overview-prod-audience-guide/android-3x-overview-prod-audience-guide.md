---
description: このガイドでは、Javaで実装されるAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。
seo-description: このガイドでは、Javaで実装されるAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。
seo-title: 製品の概要、オーディエンス、および本ガイド
title: 製品の概要、オーディエンス、および本ガイド
uuid: dd281a3e-a85f-4470-a730-2c5e87d0e490
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# 概要 {#audience}

このガイドでは、Javaで実装されるAndroid向けTVSDKを使用して、ビデオプレーヤーアプリケーションを開発する方法について説明します。

<!--<a id="section_FC24E86A2E6442B8A3769160769BBDFA"></a>-->

* TVSDKでサポートされる機能の一覧については、Primetime TVSDKの機能を参照 [してください](../../../tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-of-the-player.md)。
* TVSDKを使用するための具体的なハードウェアおよびソフトウェアの要件については、要件を参照し [てくださ](../../../tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md)い。
* 使用可能なAPIのリストについては、 [TVSDK Android APIsを参照してください](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)。

## 製品の概要 {#section_9664959F25C948878F2F7EF3D360CA95}

TVSDKには、高度なビデオ機能、コンテンツ保護、広告機能をプレーヤーに統合するのに役立つAPIの説明とコードサンプルが含まれています。 Javaを使用して、ビデオプレーヤーのユーザーインターフェイスを作成します。 TVSDKは、そのユーザーインターフェイスをそのメディアプレイヤーに接続するのに役立ちます。 これにより、メディアマニフェストに基づいてビデオや広告を再生できます。 また、TVSDKを使用して、ビデオに関する情報の取得、セキュリティの処理、再生の制御と監視を行うこともできます。

## オーディエンス {#section_527860B373734D3BA89FCF5EC1F6DC37}

このガイドは、Javaを使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 JavaでビデオプレーヤーUIを実装し、必要なTVSDK機能を組み込みます。

## このガイドについて {#section_9A5B2FC506B34B5DB71CA827B307A4D0}

このガイドでは、AndroidデバイスでJavaを使用するビデオプレーヤーにTVSDK機能を組み込むことができる情報を提供します。

## このガイドの名前空間の表記 {#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>TVSDK API名前空間の接頭辞は、簡 [!DNL com.adobe.mediacore] 潔にするために省略されることがよくあります。
>
>コンテキストが明確な場合、多くのAPI要素は親クラス指定子なしで参照されます。