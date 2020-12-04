---
description: 広告の解決と広告の読み込みによって、開始への再生を待つユーザーに許容できない遅延が発生する場合があります。 遅延広告読み込みの解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレイヤアプローチを使用して実現します。
seo-description: 広告の解決と広告の読み込みによって、開始への再生を待つユーザーに許容できない遅延が発生する場合があります。 遅延広告読み込みの解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレイヤアプローチを使用して実現します。
seo-title: ジャストインタイムの広告解決
title: ジャストインタイムの広告解決
uuid: f7b20439-3604-4d69-bdfe-2e0ad26f495b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---


# ジャストインタイム広告解決{#just-in-time-ad-resolving}

広告の解決と広告の読み込みによって、開始への再生を待つユーザーに許容できない遅延が発生する場合があります。 遅延広告読み込みの解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレイヤアプローチを使用して実現します。

**基本的な広告解決および読み込みプロセス：**

1. TVSDKはマニフェスト（プレイリスト）をダウンロードし、*すべての広告を解決*&#x200B;します。
1. TVSDK *は、すべての広告を*&#x200B;読み込み、広告セグメントをマニフェストに縫い合わせます。
1. TVSDKは、プレイヤーをPREPAREDステータスに移動し、コンテンツの再生が開始します。

プレイヤーは、マニフェスト内のURLを使用して広告コンテンツ（クリエイティブ）を取得し、広告コンテンツがTVSDKが再生できる形式になっていることを確認し、広告をタイムラインに配置します。 広告の解決と読み込みのこの基本的なプロセスは、特にマニフェストに複数の広告URLが含まれる場合、ユーザーがコンテンツの再生を待つのに許容できない長い遅延を引き起こす可能性があります。

**遅延広告の解決：**

1. TVSDKがプレイリストをダウンロードします。
1. TVSDK *は、プリロール広告を解決して*&#x200B;を読み込み、プレイヤーをPREPAREDステータスに移動し、コンテンツの再生が開始します。
1. TVSDK *は、`PTAdMetadata::delayAdLoadingTolerance`で定義されている値に基づいて、広告の位置の前に広告の時間を解決*&#x200B;します。

例えば、デフォルトで`delayAdLoadingTolerance`は5秒に設定されます。 AdBreakが3時に再生されるように設定されている場合、2:55:00に解決されます。 広告の解決に5秒以上かかると考えられる場合は、この値を増やしてください。

>[!IMPORTANT]
>
>**遅延広告解決で考慮すべき要因**
>* 遅延広告解決は、SERVER_MAP広告シグナリングモードを持つモードのVODストリームに対してのみサポートされます。
>* 遅延広告の解決は、デフォルトでは有効になっていません。 有効にするには、`PTAdMetadata::delayAdLoading` = YESに設定する必要があります。
>* 遅延広告解決は、即時オン機能と互換性がありません。 即時オンについて詳しくは、[即時オン](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md)を参照してください。
>* ピクチャインピクチャモードは、遅延広告解決ではサポートされていません。 遅延広告解決を有効にする場合は、すべてのピクチャインピクチャモードを無効にしてください。
>* 遅延広告の解決は、プリロール広告に影響しません。

>


**遅延広告解決の有効化**

遅延広告解決機能は、既存の遅延広告読み込みメカニズムを使用して有効または無効にできます（遅延広告解決はデフォルトで無効です）。

広告メタデータを設定する際に`PTAdMetadata::delayAdLoading`= YESを設定すると、遅延広告解決を有効にできます。

**遅延広告解決に関連するAPI:**

```
Class:    PTAdMetadata 
Properties: 
  
/** 
 * Property to define whether ad break resolution must be delayed until after stream start or not. 
 * When this value is NO, ads are resolved before stream start and spliced into the content when possible allowing  
   for a seamless playback experience. 
 * When this value is YES, ads are displayed in a secondary video player instance and resolved lazily only when  
   needed. 
 * Default value is NO 
 */ 
@property (nonatomic, assign) BOOL delayAdLoading; 
  
/** 
 * Property to define the lookahead for ad break resolution.  Ad breaks will be resolved when they occur between  
   the playhead time and the specified tolerance. 
 * If set to zero, the ad will be resolved immediately before playing the ad.  This may cause a slight delay in the  
   playback of the ads. 
 * Default value is 5.0 or 5 seconds. 
 */ 
  
@property (nonatomic, assign) NSTimeInterval delayAdLoadingTolerance;
```
