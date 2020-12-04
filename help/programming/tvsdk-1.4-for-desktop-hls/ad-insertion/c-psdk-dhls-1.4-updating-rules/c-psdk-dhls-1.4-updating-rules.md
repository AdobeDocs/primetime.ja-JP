---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブ選択ルールの更新
title: 広告クリエイティブ選択ルールの更新
uuid: 9eb4ccc2-425f-4c01-a095-f2043df4e25c
translation-type: tm+mt
source-git-commit: 6837c753b2f031b024ff510cda670340f346c4e1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---


# 概要{#updating-ad-creative-selection-rules}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常複数の広告クリエイティブ（`MediaFile`要素）が含まれ、それぞれが異なるコンテナコーデックのバージョンへのURLを提供します。 VAST/VMAP応答の広告クリエイティブは、それぞれ広告に対して異なるビットレートを提供する場合があります。 これらの広告クリエイティブに対して独自の優先順位と変換ルールを指定する場合は、[!DNL AdobeTVSDKConfig.json]設定ファイルで指定できます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は[!DNL AdobeTVSDKConfig.json]のままにする必要があります。
>* このファイルは、コンテンツ配信ネットワーク(CDN)でホストする必要があります。

>



[!DNL AdobeTVSDKConfig.json]では、次の2種類のルールを指定できます。*優先度*&#x200B;ルールと&#x200B;*標準化*&#x200B;ルール。
