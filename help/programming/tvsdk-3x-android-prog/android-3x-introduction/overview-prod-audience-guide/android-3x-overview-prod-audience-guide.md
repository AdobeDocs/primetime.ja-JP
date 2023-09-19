---
description: このガイドでは、Java で実装されている Android 向け TVSDK を使用して、ビデオプレーヤーアプリケーションを開発する方法に関する情報を提供します。
title: 製品の概要、オーディエンス、およびこのガイド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# 概要 {#audience}

このガイドでは、Java で実装されている Android 向け TVSDK を使用して、ビデオプレーヤーアプリケーションを開発する方法に関する情報を提供します。

<!--<a id="section_FC24E86A2E6442B8A3769160769BBDFA"></a>-->

* TVSDK でサポートされる機能の一覧については、 [Primetime TVSDK の機能](../../../tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-of-the-player.md).
* TVSDK を使用するための特定のハードウェアおよびソフトウェア要件については、 [要件](../../../tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md).
* 使用可能な API のリストについては、 [TVSDK Android API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html).

## 製品の概要 {#section_9664959F25C948878F2F7EF3D360CA95}

TVSDK には、高度なビデオ機能、コンテンツ保護、広告機能をプレーヤーに統合するのに役立つ API の説明とコードサンプルが含まれています。 Java を使用して、ビデオプレーヤーのユーザーインターフェイスを作成します。 TVSDK は、このユーザーインターフェイスをメディアプレーヤーに接続するのに役立ちます。 これにより、メディアマニフェストに基づいてビデオや広告を再生できます。 また、 TVSDK を使用して、ビデオに関する情報を取得し、セキュリティを処理して、再生を制御および監視することもできます。

## 対象ユーザ {#section_527860B373734D3BA89FCF5EC1F6DC37}

このガイドは、Java を使用したアプリケーションおよびビデオプレーヤーの開発方法を理解していることを前提としています。 ビデオプレーヤー UI を Java に実装し、必要な TVSDK 機能を組み込みます。

## このガイドについて {#section_9A5B2FC506B34B5DB71CA827B307A4D0}

このガイドでは、Android デバイスで Java を使用してビデオプレーヤーに TVSDK 機能を組み込むことができる情報を提供します。

## このガイドの名前空間表記 {#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>TVSDK API 名前空間のプレフィックス [!DNL com.adobe.mediacore] 多くの場合、簡潔にするためには省略されます。
>
>コンテキストが明確な場合、多くの API 要素は、親クラス指定子を付けずに参照されます。
