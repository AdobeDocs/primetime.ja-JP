---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブの選択ルールの更新
title: 広告クリエイティブの選択ルールの更新
uuid: 77d8e186-01b5-4d62-8686-28f431d18876
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# 概要 {#update-ad-creative-selection-rules-overview}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常、複数の広告クリエイティブ（要素）が含まれ、各クリエイティブは異なるコンテナコーデックのバージョンへのURLを提供します。 `MediaFile` 場合によっては、VAST/VMAP応答の広告クリエイティブがそれぞれ異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先順位と変換ルールを指定する場合は、設定ファイルで指定で [!DNL AdobeTVSDKConfig.json] きます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は残す必要があ [!DNL AdobeTVSDKConfig.json]る。
>* このファイルは、プロジェクトのフォルダ [!DNL assets/] に配置する必要があります。
>* 広告の再生中にオーディオトラックを変更しても、オーディオトラックは変更されません。 広告の再生中にユーザーがオーディオトラックを変更することを許可しないでください。
>



では、次の2種類のルールを指定できま [!DNL AdobeTVSDKConfig.json]す。優先度ル *ール* と標準化 *ルール* 。

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

広告ルールはJSONファイルを使用して指定します。 JSONファイルの形式は、TVSDKの両方のバージョンで同じままです。 ただし、TVSDK v3.0では、広告ルールJSONファイルは、HTTP URLを介してアクセス可能な場所でホストされている必要があります。 アプリケーションは、AuditudeSettingsのインスタンスを使用できます。

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
