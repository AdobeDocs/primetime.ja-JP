---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブ選択ルールの更新
title: 広告クリエイティブ選択ルールの更新
uuid: 77d8e186-01b5-4d62-8686-28f431d18876
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# 概要{#update-ad-creative-selection-rules-overview}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常複数の広告クリエイティブ（`MediaFile`要素）が含まれ、それぞれが異なるコンテナコーデックのバージョンへのURLを提供します。 VAST/VMAP応答の広告クリエイティブは、それぞれ広告に対して異なるビットレートを提供する場合があります。 これらの広告クリエイティブに対して独自の優先順位と変換ルールを指定する場合は、[!DNL AdobeTVSDKConfig.json]設定ファイルで指定できます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は[!DNL AdobeTVSDKConfig.json]のままにする必要があります。
>* このファイルは、プロジェクトの[!DNL assets/]フォルダーに配置する必要があります。
>* 広告の再生中にオーディオトラックを変更しても、オーディオトラックは変更されません。 広告の再生中にユーザーがオーディオトラックを変更することを許可しないでください。

>



[!DNL AdobeTVSDKConfig.json]では、次の2種類のルールを指定できます。*優先度*&#x200B;ルールと&#x200B;*標準化*&#x200B;ルール。

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

広告ルールはJSONファイルを使用して指定されます。 JSONファイルの形式は、TVSDKの両方のバージョンで同じままです。 ただし、TVSDK v3.0では、広告ルールのJSONファイルは、HTTP URLを介してアクセス可能な場所でホストする必要があります。 アプリケーションは、AuditudeSettingsのインスタンスを使用できます。

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
