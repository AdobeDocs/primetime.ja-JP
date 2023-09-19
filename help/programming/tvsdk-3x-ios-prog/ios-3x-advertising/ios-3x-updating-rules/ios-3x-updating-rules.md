---
description: TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。
keywords: クリエイティブ選択ルール；AdobeTVSDKConfig;Ad Creative 優先度；変換ルール
title: 広告クリエイティブの選択ルールを更新
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 概要 {#update-ad-creative-selection-rules-overview}

TVSDK 設定ファイル (AdobeTVSDKConfig.json) を使用して、VAST/VMAP 応答の広告クリエイティブ選択の優先度を更新できます。 また、この設定ファイルを使用して、広告クリエイティブのソース URL 変換ルールを定義することもできます。

ビデオプレーヤーが広告サーバーにリクエストをおこなうと、VAST/VMAP の応答には通常、複数の広告クリエイティブ ( `MediaFile` 要素 ) を含み、それぞれが異なるコンテナコーデックバージョンへの URL を提供します。 場合によっては、VAST/VMAP 応答の広告クリエイティブがそれぞれ、広告に対して異なるビットレートを提供します。 これらの広告クリエイティブに独自の優先度と変換ルールを指定する場合は、 [!DNL AdobeTVSDKConfig.json] 設定ファイル。

>[!IMPORTANT]
>
>* TVSDK 設定ファイルの名前は変更しないでください。 名前は残る必要があります [!DNL AdobeTVSDKConfig.json].
>* このファイルは、バンドルにアクセス可能な任意の場所に配置できます。
>

では、2 種類のルールを指定できます [!DNL AdobeTVSDKConfig.json]: *優先度* ルールと *Normalize* ルール。

**[!UICONTROL Disabling Pre-Roll]**

プリロールを無効にするには、デフォルトのオポチュニティジェネレーターを変更して、プリロール呼び出しをおこなわないようにする必要があります。 デフォルトでは、 TVSDK は以下のオポチュニティジェネレーターを使用します。

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

ライブストリームでのプリロールを無効にするには、SpliceOutOpportunityGenerator のみを含めるように変更します。

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
