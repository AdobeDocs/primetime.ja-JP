---
description: 広告の解決と広告の読み込みによって、ユーザーが再生を開始するのを待つのに許容できない遅延が発生する場合があります。 遅延広告読み込み解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレーヤーアプローチを使用して行います。
seo-description: 広告の解決と広告の読み込みによって、ユーザーが再生を開始するのを待つのに許容できない遅延が発生する場合があります。 遅延広告読み込み解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレーヤーアプローチを使用して行います。
seo-title: ジャストインタイムの広告解決
title: ジャストインタイムの広告解決
uuid: f7b20439-3604-4d69-bdfe-2e0ad26f495b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# ジャストインタイムの広告解決 {#just-in-time-ad-resolving}

広告の解決と広告の読み込みによって、ユーザーが再生を開始するのを待つのに許容できない遅延が発生する場合があります。 遅延広告読み込み解決機能を使用すると、この起動遅延を減らすことができます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレーヤーアプローチを使用して行います。

**基本的な広告解決および読み込みプロセス：**

1. TVSDKは、マニフェスト（プレイリスト）をダウンロ *ードし* 、すべての広告を解決します。
1. TVSDKは、す *べての広告* を読み込み、広告セグメントをマニフェストに縫い合わせます。
1. TVSDKは、プレイヤーをPREPAREDステータスに移動し、コンテンツの再生を開始します。

プレイヤーはマニフェスト内のURLを使用して広告コンテンツ（クリエイティブ）を取得し、広告コンテンツがTVSDKが再生できる形式になるようにし、TVSDKは広告をタイムラインに配置します。 広告の解決と読み込みのこの基本的なプロセスにより、特にマニフェストに複数の広告URLが含まれている場合、ユーザーがコンテンツを再生するのを待つのに許容できない長い遅延が発生する可能性があります。

**遅延広告解決：**

1. TVSDKは、プレイリストをダウンロードします。
1. TVSDKは、プ *リロール広告を解決* 、読み込み、プレイヤーをPREPAREDステータスに移動し、コンテンツの再生が開始します。
1. TVSDKは ** 、で定義された値に基づいて、各広告の時間をその位置の前に解決しま `PTAdMetadata::delayAdLoadingTolerance`す。

例えば、デフォルトでは5 `delayAdLoadingTolerance` 秒に設定されています。 AdBreakが3時に再生されるように設定されている場合、2:55:00に解決されます。 広告の解像度が5秒以上かかると考えられる場合は、この値を増やします。

>[!IMPORTANT]
>
>**遅延広告解決で考慮すべき要因：**
>* 遅延広告解決は、モードSERVER_MAP広告シグナリングモードを持つVODストリームに対してのみサポートされます。
>* 遅延広告の解決は、デフォルトでは有効になっていません。 有効にするには、 `PTAdMetadata::delayAdLoading` = YESを設定する必要があります。
>* 遅延広告解決は、即時オン機能と互換性がありません。 即時オンの詳細については、「即時オン」を参 [照してください](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md)。
>* ピクチャインピクチャモードは、遅延広告解決ではサポートされていません。 遅延広告解決を有効にした場合は、ピクチャインピクチャモードを無効にしてください。
>* 遅延広告の解決は、プリロール広告に影響を与えません。
>


**遅延広告解決の有効化**

既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（デフォルトでは、遅延広告解決は無効になっています）。

広告メタデータを設定する際に、 `PTAdMetadata::delayAdLoading`= YESを設定して、遅延広告解決を有効にできます。

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
