---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブ選択ルールの更新
title: 広告クリエイティブ選択ルールの更新
uuid: b7d316ef-323e-4769-83d9-036422ae1707
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---


# 概要{#update-ad-creative-selection-rules-overview}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常複数の広告クリエイティブ（`MediaFile`要素）が含まれ、それぞれが異なるコンテナコーデックのバージョンへのURLを提供します。 VAST/VMAP応答の広告クリエイティブは、それぞれ広告に対して異なるビットレートを提供する場合があります。 これらの広告クリエイティブに対して独自の優先順位と変換ルールを指定する場合は、[!DNL AdobeTVSDKConfig.json]設定ファイルで指定できます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は[!DNL AdobeTVSDKConfig.json]のままにする必要があります。
>* このファイルは、バンドルにアクセス可能な任意の場所に配置できます。

>



[!DNL AdobeTVSDKConfig.json]では、次の2種類のルールを指定できます。*優先度*&#x200B;ルールと&#x200B;*標準化*&#x200B;ルール。

**[!UICONTROL Disabling Pre-Roll]**

プリロールを無効にするには、デフォルトのオポチュニティジェネレーターを変更して、プリロール呼び出しを行わないようにする必要があります。 デフォルトでは、TVSDKは次のオポチュニティジェネレーターを使用します。

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    result.push(new AdSignalingModeOpportunityGenerator()); 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
} 
```

ライブストリームのプリロールを無効にするには、SpliceOutOpportunityGeneratorのみを含めるように変更する必要があります。

```
/** 
 * @inheritDoc 
 */ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
    var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
    if (preroll_enabled == true) { 
        result.push(new AdSignalingModeOpportunityGenerator()); 
    } 
    result.push(new SpliceOutOpportunityGenerator()); 
    return result; 
}
```
