---
description: TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。
keywords: クリエイティブ選択ルール；AdobeTVSDKConfig；広告クリエイティブプロパティ；変換ルール
title: 広告クリエイティブ選択ルールの更新
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# 概要{#updating-ad-creative-selection-rules-overview}

TVSDK設定ファイル(AdobeTVSDKConfig.json)を使用して、VAST/VMAP応答で広告クリエイティブを選択するための優先順位を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソースURL変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストを行う場合、VAST/VMAPの応答には通常複数の広告クリエイティブ（`MediaFile`要素）が含まれ、それぞれが異なるコンテナコーデックのバージョンへのURLを提供します。 VAST/VMAP応答の広告クリエイティブは、それぞれ広告に対して異なるビットレートを提供する場合があります。 これらの広告クリエイティブに対して独自の優先順位と変換ルールを指定する場合は、[!DNL AdobeTVSDKConfig.json]設定ファイルで指定できます。

>[!IMPORTANT]
>
>* TVSDK設定ファイルの名前は変更しないでください。 名前は[!DNL AdobeTVSDKConfig.json]のままにする必要があります。
>* このファイルは、プロジェクトの[!DNL assets/]フォルダーに配置する必要があります。

>



[!DNL AdobeTVSDKConfig.json]では、次の2種類のルールを指定できます。*優先度*&#x200B;ルールと&#x200B;*標準化*&#x200B;ルール。

## プリロールを無効にする{#disabling-preroll}

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

