---
description: 広告の解決と広告の読み込みにより、ユーザーが再生を開始するのを待つのに許容できない遅延が生じる場合があります。 遅延広告読み込みの解決機能を使用すると、この起動遅延を短縮できます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレーヤーアプローチを使用して実現します。
title: ジャストインタイムの広告解決
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ジャストインタイムの広告解決 {#just-in-time-ad-resolving}

広告の解決と広告の読み込みにより、ユーザーが再生を開始するのを待つのに許容できない遅延が生じる場合があります。 遅延広告読み込みの解決機能を使用すると、この起動遅延を短縮できます。 広告の時間の位置より前に、指定した間隔で広告を解決できるようになりました。 これは、デュアルプレーヤーアプローチを使用して実現します。

**基本的な広告の解決と読み込みプロセス：**

1. TVSDK は、マニフェスト（プレイリスト）をダウンロードし、 *解決済み* すべての広告。
1. TVSDK *負荷* すべての広告を使用して、広告セグメントをマニフェストにステッチします。
1. TVSDK は、プレーヤーを PREPARED ステータスに移動し、コンテンツの再生を開始します。

プレーヤーは、マニフェスト内の URL を使用して広告コンテンツ（クリエイティブ）を取得し、TVSDK が再生できる形式の広告コンテンツを提供し、 TVSDK が広告をタイムラインに配置します。 広告の解決と読み込みのこの基本的なプロセスにより、特にマニフェストに複数の広告 URL が含まれている場合に、ユーザーがコンテンツの再生を待機するのに許容できない長い時間がかかる可能性があります。

**遅延広告解決：**

1. TVSDK はプレイリストをダウンロードします。
1. TVSDK *解決および読み込み* プリロール広告が発生すると、プレーヤーは PREPARED ステータスに移行し、コンテンツの再生が開始します。
1. TVSDK *解決済み* 各広告は、 `PTAdMetadata::delayAdLoadingTolerance`.

例えば、デフォルトでは `delayAdLoadingTolerance` が 5 秒に設定されている場合、 広告ブレークの再生が 3:00 に設定されている場合、2 時に解決されます:55:00. 広告の解決に 5 秒以上かかると思われる場合は、この値を増やします。

>[!IMPORTANT]
>
>**遅延広告解決で考慮すべき要因：**
>* 遅延広告解決は、SERVER_MAP 広告シグナリングモードを持つモードの VOD ストリームでのみサポートされます。
>* 遅延広告解決は、デフォルトでは有効になっていません。 次を設定する必要があります： `PTAdMetadata::delayAdLoading` =有効にする場合ははい。
>* 遅延広告解決は、インスタントオン機能と互換性がありません。 Instant On の詳細については、 [即時オン](../../tvsdk-3x-ios-prog/ios-3x-instant-on-ios.md).
>* ピクチャーインピクチャーモードは、遅延広告解決ではサポートされていません。 遅延広告解決を有効にした場合は、ピクチャインピクチャモードを無効にしてください。
>* 遅延広告解決は、プリロール広告には影響しません。
>
**遅延広告解決を有効にする**

既存の遅延広告読み込みメカニズムを使用して、遅延広告解決機能を有効または無効にできます（遅延広告解決はデフォルトで無効になっています）。

遅延広告解決を有効にするには、 `PTAdMetadata::delayAdLoading`=はい（広告メタデータの設定時）

**遅延広告解決に関連する API:**

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
