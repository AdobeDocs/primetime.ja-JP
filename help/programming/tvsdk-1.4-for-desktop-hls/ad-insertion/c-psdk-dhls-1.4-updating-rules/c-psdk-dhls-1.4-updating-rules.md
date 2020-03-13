---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブの選択ルールの更新
title: 広告クリエイティブの選択ルールの更新
uuid: 9eb4ccc2-425f-4c01-a095-f2043df4e25c
translation-type: tm+mt
source-git-commit: 6837c753b2f031b024ff510cda670340f346c4e1

---


# 概要 {#updating-ad-creative-selection-rules}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常、複数の広告クリエイティブ（要素）が含まれ、各クリエイティブは異なるコンテナコーデックのバージョンへのURLを提供します。 `MediaFile` 場合によっては、VAST/VMAP応答の広告クリエイティブがそれぞれ異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先順位と変換ルールを指定する場合は、設定ファイルで指定で [!DNL AdobeTVSDKConfig.json] きます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は残す必要があ [!DNL AdobeTVSDKConfig.json]る。
>* このファイルは、コンテンツ配信ネットワーク(CDN)でホストする必要があります。
>



では、次の2種類のルールを指定できま [!DNL AdobeTVSDKConfig.json]す。優先度ル *ール* と標準化 *ルール* 。
