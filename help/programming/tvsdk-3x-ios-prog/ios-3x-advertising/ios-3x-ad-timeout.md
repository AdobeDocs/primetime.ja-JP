---
description: Adobe Primetime Ad Decisioning インターフェイスを使用して、VOD およびライブ/リニアコンテンツに広告を挿入できます。
title: 広告要件
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# 広告タイムアウト {#ad-timeout}

## AV Foundation の要件 {#av-foundation-requirements}

VOD コンテンツの場合、メインコンテンツマニフェストの読み込み、広告の解決、広告マニフェストの読み込みを含むプレイリストのステッチは、35 秒以内に完了する必要があります。

ライブコンテンツの場合、プレイリストが更新されるたびに、プレイリストのステッチを 20 秒以内に完了する必要があります

**AdResolution タイムアウトに関連する API**

```
/** @name Properties */
/** The default timeout value (in seconds) for resolution of ad requests is 15 seconds.
*
*/
*
@property (notatomic, assign) double adResolutionTimeout;
```

adResolutionTimeout は、広告メタデータの設定時に PTAdMetadata::adResolutionTimeout を設定して設定できます。

```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adResolutionTimeout = 15 seconds
```

その後は、次の手順に従います。 [Primetime 広告サーバーメタデータ](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).

**AdManifest タイムアウトに関連する API**

```
/** @name Properties */
 /** The default timeout value (in seconds) for loading of ad manifests is 5 seconds.
 *
 */
 *
 @property (notatomic, assign) double adManifestTimeout; 
```

adManifestTimeout は、広告メタデータの設定時に PTAdMetadata::adManifestTimeout を設定することで設定できます。


```
// Create an instance of PTAuditudeMetadata and set its property
PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init]autorelease];;
adMetadata.adManifestTimeout = 5 seconds
```

その後は、次の手順に従います。 [Primetime 広告サーバーメタデータ](/help/programming/tvsdk-3x-ios-prog/ios-3x-advertising/ios-3x-primetime-ad-serving-metadata/ios-3x-primetime-ad-serving-metadata.md).
