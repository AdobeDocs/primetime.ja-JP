---
description: 広告挿入は、広告をビデオオンデマンド(VOD)、ライブストリーミング、および広告トラッキングと広告再生を含むリニアストリーミング用に解決します。 TVSDKは、広告サーバーに必要なリクエストを行い、指定されたコンテンツの広告に関する情報を受信し、コンテンツ内の広告を各フェーズで配置します。
title: 広告の挿入
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# 概要{#inserting-ads-overview}

広告挿入は、広告をビデオオンデマンド(VOD)、ライブストリーミング、および広告トラッキングと広告再生を含むリニアストリーミング用に解決します。 TVSDKは、広告サーバーに必要なリクエストを行い、指定されたコンテンツの広告に関する情報を受信し、コンテンツ内の広告を各フェーズで配置します。

*`ad break`*&#x200B;には、1つ以上の広告が順に再生されます。 TVSDKは、1つ以上の広告の時間のメンバーとして、メインコンテンツに広告を挿入します。

## プリロール広告を無効にする{#disable-preroll-ads}

プリロールを無効にするには、デフォルトのオポチュニティジェネレーターを変更して、プリロール呼び出しを行わないようにします。 デフォルトのオポチュニティジェネレーターは次のとおりです。

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
result.push(new AdSignalingModeOpportunityGenerator()); 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```

ライブストリームのプリロールを無効にするには、上記を変更してSpliceOutOpportunityGeneratorのみを含めます。

```
@inheritDoc 
*/ 
override protected function doRetrieveGenerators(item:MediaPlayerItem):Vector.<OpportunityGenerator> { 
var result:Vector.<OpportunityGenerator> = new Vector.<OpportunityGenerator>(); 
if (preroll_enabled == true) { result.push(new AdSignalingModeOpportunityGenerator()); } 
 
result.push(new SpliceOutOpportunityGenerator()); 
return result; 
}
```
