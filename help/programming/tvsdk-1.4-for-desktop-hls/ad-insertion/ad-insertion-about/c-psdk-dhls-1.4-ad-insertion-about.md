---
description: 広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。
seo-description: 広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。
seo-title: 広告の挿入
title: 広告の挿入
uuid: 25c79822-a861-427b-b6a8-24714b21aae4
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# 概要 {#inserting-ads-overview}

広告挿入は、ビデオオンデマンド(VOD)、ライブストリーミング、および広告追跡と広告再生を含むリニアストリーミング用の広告を解決します。 TVSDKは、広告サーバーに対して必要なリクエストを行い、指定したコンテンツの広告に関する情報を受信し、コンテンツ内の広告をフェーズ別に配置します。

「」には、 *`ad break`* 順番に再生される1つ以上の広告が含まれます。 TVSDKは、1つ以上の広告の時間のメンバーとして、メインコンテンツに広告を挿入します。

## プリロール広告の無効化 {#disable-preroll-ads}

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

ライブストリームのプリロールを無効にするには、SpliceOutOpportunityGeneratorのみを含めるように上記を変更します。

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
