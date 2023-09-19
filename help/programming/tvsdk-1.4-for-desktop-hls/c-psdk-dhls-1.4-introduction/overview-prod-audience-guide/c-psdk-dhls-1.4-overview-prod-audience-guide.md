---
description: このガイドでは、TVSDK for Desktop HLS を使用してビデオプレーヤーアプリケーションを開発する方法について説明します。HLS はActionScriptで実装されています。
title: 概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# 概要 {#overview}

このガイドでは、TVSDK for Desktop HLS を使用してビデオプレーヤーアプリケーションを開発する方法について説明します。HLS はActionScriptで実装されています。

## 製品の概要 {#section_9664959F25C948878F2F7EF3D360CA95}

TVSDK には、高度なビデオ機能、コンテンツ保護、広告機能をプレーヤーに統合するのに役立つ API の説明とコードサンプルが含まれています。 ActionScriptを使用して、ビデオプレーヤーのユーザーインターフェイスを作成します。 TVSDK は、このユーザーインターフェイスをメディアプレーヤーに接続するのに役立ちます。 これにより、メディアマニフェストに基づいてビデオや広告を再生できます。 また、 TVSDK を使用して、ビデオに関する情報を取得し、セキュリティを処理して、再生を制御および監視することもできます。

TVSDK を使用するための特定のハードウェアおよびソフトウェア要件については、 [要件](../../c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/r-psdk-dhls-1.4-requirements-system.md).

## 対象ユーザ {#section_527860B373734D3BA89FCF5EC1F6DC37}

このガイドは、ActionScriptを使用したアプリケーションやビデオプレーヤーの開発方法を理解していることを前提としています。 その言語を使用してビデオプレーヤーのユーザーインターフェイスを実装し、TVSDK 機能を組み込みます。

## このガイドについて {#section_9A5B2FC506B34B5DB71CA827B307A4D0}

このガイドでは、デスクトップマシンでActionScriptを使用して TVSDK 機能をビデオプレーヤーに組み込むことができる情報を提供します。

## このガイドの名前空間表記 {#section_8B866054E9ED4B5F99DCA7A681404632}

>[!TIP]
>
>TVSDK API 名前空間のプレフィックス `com.adobe.mediacore` は簡潔にするために省略されます。
>
>コンテキストが明確な場合、多くの API 要素は、親クラス指定子を付けずに参照されます。
