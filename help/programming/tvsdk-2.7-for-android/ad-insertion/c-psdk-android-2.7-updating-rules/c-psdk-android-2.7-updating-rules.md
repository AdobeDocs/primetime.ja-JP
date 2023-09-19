---
description: TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。
keywords: クリエイティブ選択ルール；AdobeTVSDKConfig;Ad Creative 優先度；変換ルール
title: 広告クリエイティブの選択ルールを更新
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# 概要 {#update-ad-creative-selection-rules-overview}

TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストをおこなうと、VAST/VMAP の応答には通常、複数の広告クリエイティブ ( `MediaFile` 要素 ) を含み、それぞれが異なるコンテナコーデックバージョンへの URL を提供します。 場合によっては、VAST/VMAP 応答の広告クリエイティブがそれぞれ、広告に対して異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先度と変換ルールを指定する場合は、 [!DNL AdobeTVSDKConfig.json] 設定ファイル。

>[!IMPORTANT]
>
>* TVSDK 設定ファイルの名前は変更しないでください。 名前は残る必要があります [!DNL AdobeTVSDKConfig.json].
>* このファイルは、 [!DNL assets/] プロジェクトのフォルダー。
>* 広告の再生中にオーディオトラックを変更しても、オーディオトラックは変更されません。 プレーヤーでは、広告の再生時にユーザーがオーディオトラックを変更することを許可しないでください。
>

では、2 種類のルールを指定できます [!DNL AdobeTVSDKConfig.json]: *優先度* ルールと *Normalize* ルール。

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

広告ルールは JSON ファイルを使用して指定されます。 JSON ファイルの形式は、両方のバージョンの TVSDK で同じになります。 ただし、TVSDK v2.5 では、広告ルールの JSON ファイルは、HTTP URL を介してアクセス可能な場所でホストする必要があります。 アプリケーションは、AuditudeSettings のインスタンスを使用できます。

```
//TVSDK v2.5 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
