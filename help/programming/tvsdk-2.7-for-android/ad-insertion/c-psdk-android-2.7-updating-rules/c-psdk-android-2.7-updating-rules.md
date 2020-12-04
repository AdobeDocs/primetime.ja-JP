---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブ選択ルールの更新
title: 広告クリエイティブ選択ルールの更新
uuid: fddc5593-db40-4b03-bd7e-4b5fe5b6f650
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7
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

広告ルールはJSONファイルを使用して指定されます。 JSONファイルの形式は、TVSDKの両方のバージョンで同じままです。 ただし、TVSDK v2.5では、広告ルールのJSONファイルは、HTTP URLを介してアクセス可能な場所でホストする必要があります。 アプリケーションは、AuditudeSettingsのインスタンスを使用できます。

```
//TVSDK v2.5 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```

