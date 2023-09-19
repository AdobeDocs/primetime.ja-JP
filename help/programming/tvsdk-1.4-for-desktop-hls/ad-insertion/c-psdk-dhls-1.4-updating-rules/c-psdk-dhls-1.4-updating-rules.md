---
description: TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。
title: 広告クリエイティブ選択ルールの更新
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# 概要 {#updating-ad-creative-selection-rules}

TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストをおこなうと、VAST/VMAP の応答には通常、複数の広告クリエイティブ ( `MediaFile` 要素 ) を含み、それぞれが異なるコンテナコーデックバージョンへの URL を提供します。 場合によっては、VAST/VMAP 応答の広告クリエイティブがそれぞれ、広告に対して異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先度と変換ルールを指定する場合は、 [!DNL AdobeTVSDKConfig.json] 設定ファイル。

>[!IMPORTANT]
>
>* TVSDK 設定ファイルの名前は変更しないでください。 名前は残る必要があります [!DNL AdobeTVSDKConfig.json].
>* このファイルは、コンテンツ配信ネットワーク (CDN) でホストする必要があります。
>

では、2 種類のルールを指定できます [!DNL AdobeTVSDKConfig.json]: *優先度* ルールと *Normalize* ルール。
