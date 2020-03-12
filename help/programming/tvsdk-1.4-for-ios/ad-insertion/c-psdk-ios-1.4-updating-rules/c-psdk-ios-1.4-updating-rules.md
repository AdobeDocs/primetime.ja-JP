---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: creative selection rules;AdobeTVSDKConfig;ad creative priorities;transformation rules
seo-description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
seo-title: 広告クリエイティブの選択ルールの更新
title: 広告クリエイティブの選択ルールの更新
uuid: c33fe1f0-78cb-4dc2-89d2-e9fb1bf0e73f
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 概要 {#update-ad-creative-selection-rules-overview}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブの選択の優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常、複数の広告クリエイティブ（要素）が含まれ、各クリエイティブは異なるコンテナコーデックのバージョンへのURLを提供します。 `MediaFile` 場合によっては、VAST/VMAP応答の広告クリエイティブがそれぞれ異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先順位と変換ルールを指定する場合は、設定ファイルで指定で [!DNL AdobeTVSDKConfig.json] きます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は残す必要があ [!DNL AdobeTVSDKConfig.json]る。
>* このファイルは、バンドルにアクセスできる任意の場所に配置できます。
>



では、次の2種類のルールを指定できま [!DNL AdobeTVSDKConfig.json]す。優先度ル *ール* と標準化 *ルール* 。

**[!UICONTROL Disabling Pre-Roll]**

プリロールを無効にするには、プリロール呼び出しを行わないようにデフォルトのオポチュニティジェネレーターを変更する必要があります。 デフォルトでは、TVSDKは次のオポチュニティジェネレーターを使用します。

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

