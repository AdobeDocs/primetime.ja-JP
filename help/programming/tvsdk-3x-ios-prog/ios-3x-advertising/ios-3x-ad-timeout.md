---
description: Adobe Primetimeのad decisioningインターフェイスを使用して、VODおよびライブ/リニアコンテンツに広告を挿入できます。
title: 広告の要件
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# 広告タイムアウト{#ad-timeout}

## AVファンデーションの要件{#av-foundation-requirements}

VODコンテンツの場合、メインコンテンツマニフェストの読み込み、広告の解決、広告マニフェストの読み込みを含むプレイリストのステッチは、35秒以内に完了する必要があります。

Liveコンテンツの場合、プレイリストが更新されるたびに、プレイリストのステッチが20秒以内に完了する必要があります

**AdResolutionのタイムアウトに関連するAPI**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

広告メタデータを設定する際に、PTAdMetadata::adResolutionTimeoutを設定してadResolutionTimeoutを設定できます。

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

その後、次の節に従います。[Primetime広告サーバーメタデータ](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md)。

**AdManifestのタイムアウトに関連するAPI**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

広告メタデータを設定する際に、PTAdMetadata::adManifestTimeoutを設定することで、adManifestTimeoutを設定できます。


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

その後、次の節に従います。[Primetime広告サーバーメタデータ](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md)。
