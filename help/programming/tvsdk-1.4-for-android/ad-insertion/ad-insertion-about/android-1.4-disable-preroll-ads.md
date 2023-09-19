---
title: プリロール広告を無効にする
description: プリロール広告を無効にする
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '43'
ht-degree: 0%

---

# プリロール広告を無効にする{#disable-pre-roll-ads}

プリロールを無効にするには、デフォルトのオポチュニティジェネレーターを変更して、プリロール呼び出しをおこなわないようにします。 デフォルトのオポチュニティジェネレーターは次のとおりです。

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

ライブストリームでのプリロールを無効にするには、上記を変更して SpliceOutOpportunityGenerator のみを含めます。

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
