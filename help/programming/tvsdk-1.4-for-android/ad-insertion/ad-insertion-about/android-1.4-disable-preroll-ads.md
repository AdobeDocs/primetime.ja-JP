---
description: 'null'
seo-description: 'null'
seo-title: プリロール広告の無効化
title: プリロール広告の無効化
uuid: 2e307a58-49f2-43d6-908b-97684ad6e3d3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '45'
ht-degree: 0%

---


# プリロール広告の無効化{#disable-pre-roll-ads}

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

