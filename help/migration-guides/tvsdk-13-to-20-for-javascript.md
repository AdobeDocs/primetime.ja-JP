---
title: TVSDK変換 — JavaScriptの場合は1.3 ～ 2.0
seo-title: TVSDK変換 — JavaScriptの場合は1.3 ～ 2.0
description: 多くのメソッドの署名とAPI要素名が2.0で変更されました。これらの表を確認して、APIの変更の詳細をすべて確認してください。
seo-description: 多くのメソッドの署名とAPI要素名が2.0で変更されました。これらの表を確認して、APIの変更の詳細をすべて確認してください。
uuid: d2d1742d-c90c-43f5-94fc-8c4a57cb8ed4
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
discoiquuid: c732f54d-116c-43f3-bec4-5e71af208426
translation-type: tm+mt
source-git-commit: cfd6da49e85e13e29e8458ee98231a8b476867db
workflow-type: tm+mt
source-wordcount: '5058'
ht-degree: 0%

---


# TVSDK変換 — JavaScriptの場合は1.3 ～ 2.0 {#tvsdk-conversion-to-for-javascript}

多くのメソッドの署名とAPI要素名が2.0で変更されました。これらの表を確認して、APIの変更の詳細をすべて確認してください。

## JavaScriptでのコールバック関数の実装 {#implement-callback-functions-in-javascript}

メソッドのドキュメント内のコメントは、実装する必要があるコールバックの署名を示します。

JavaScriptの場合、API構文はWeb IDに基づきます。 TVSDKインターフェイスの場合、メソッド名は *methodName*()と呼ばれます。 アプリケーションで実装するメソッドの場合は、methodNameCallbackFuncという読み取り/書き込み属性がインターフェイスに追加され、 **&#x200B;メソッドを実装する関数を指すようにアプリケーションで設定する必要があります。 例：

```shell
// An app implementable interface
interface ContentFactory
{
    /*
     * AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item);
     */
    attribute Object retrieveAdPolicySelectorCallbackFunc;
 
    /*
     * ContentResolverList retrieveResolvers(MediaPlayerItem item);
     */
    attribute Object retrieveResolversCallbackFunc;
 
    /*
     * OpportunityGeneratorList retrieveGenerators(MediaPlayerItem item);
     */
    attribute Object retrieveGeneratorsCallbackFunc;
};

// this is how to implement it
var factory = new AdobePSDK.ContentFactory();
factory.retrieveAdPolicySelectorCallbackFunc = function(item)
{
    // return your adPolicySelector according to the item
    return adPolicySelector;
}
 
mediaPlayerItemConfig = new AdobePSDK.MediaPlayerItemConfig ();
playerConfig.adFactory = factory;
// Use this config to load new MediaResource
```

## 2.0での広告ワークフローAPI要素の変更 {#advertising-workflow-api-element-changes-for}

次の表に、JavaScript TVSDKの広告ワークフローAPIエレメントを、バージョン1.3と2.0で比較します。

このトピックの表：

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* 配置
* オポチュニティ
* 予約
* Timeline/TimelineItem/TimelineMarker
* AdBreak
* 広告/AdAsset/AdClick/AdList/AdAssetList/AdBannerAsset
* AdBreakTimelineItem / AdTimelineItem
* AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector
* TimelineOperation
* AdBreakPlacement
* AuditudeSettings

### TimedMetadata {#timedmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>TimedMetadata</strong>:interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1 ; <br /> readonly属性unsigned short型； <br /> readonly属性の長い時間。<br /> readonly attribute DomString id;<br /> readonly attribute DomString name;<br /> readonly attribute DomString content; <br /> readonly attribute object metadata;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly attribute unsigned short metadataType;<br /> readonly属性の長い時間。<br /> readonly属性long id;<br /> readonly attribute DomString name;<br /><br /> readonly attribute object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>:（2.0では変更はありません）</td> 
   <td><p>interface TimedMetadataList {<br /> readonly attribute unsigned long length;<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdSignalingMode {#adsignalingmode}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>インターフェイスAdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES, <br /> const unsigned short MODE_SERVER_MAP, const unsigned short MODE_CUSTOM_RANGES <br /><br /> };</p> </td> 
   <td>これは、MetadataKeys::MANIFEST_CUESキーを置き換えます。</td> 
  </tr> 
 </tbody> 
</table>

### AdvertisingMetadata {#advertisingmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface AdvertisingMetadata { <br /> attribute AdSignalingMode; <br /> attribute AdBreakWatchedPolicy adBreakAsWatched; <br /> attribute boolean livePreroll; <br /> attribute boolean delayAdLoading ; <br /> };</p> </td> 
   <td>この機能は、<p>MetadataKeys::ADVERTISING_METADATA</p> キー。</td> 
  </tr> 
 </tbody> 
</table>

### CustomRangeMetadata {#customrangemetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_DELETE_RANGE; <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> attribute unsigned short type; <br /> attribute boolean adjustSeekPosition; <br /> attribute TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### ReplaceTimeRange {#replacetimerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ReplaceTimeRange { <br /> attribute unsigned long begin; <br /> readonly属性unsigned long end; <br /> attribute unsigned long duration; <br /> attribute unsigned long replaceDuration; <br /> };</p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### 配置 {#placement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>Interface Placement { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_POST_ROLL; <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly属性unsigned short型； <br /> readonly属性の長い時間。 <br /> readonly属性long duration; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_DELETE; <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> readonly属性unsigned shortモード； <br /> readonly attribute TimeRange range; <br /> };</p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### オポチュニティ {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Opportunity { <br /> readonly attribute DomString id; <br /> readonly属性の配置； <br /> readonly attribute object settings; <br /> readonly attribute object customParameters; <br /> }; </p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### 予約 {#reservation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Reservation { <br /> readonly attribute TimeRange; <br /> readonly属性の長い保持期間。 <br /> }; </p> </td> 
   <td> （2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### Timeline/TimelineItem/TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>タイムライン</strong>:interface Timeline <br /> { readonly attribute TimelineMarkerList timelineMarkers; <br /> readonly attribute timelineItemList timelineItems; <br /> 重複convertToLocalTime(重複時間); <br /> 重複convertToVirtualTime(重複時間); <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly attribute TimelineMarkerList timelineMarkers;<br /><br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>:interface TimelineItem :<br /> TimelineMarker {<br /> readonly attribute long id; <br /> readonly attribute TimeRange virtualRange; <br /> readonly attribute TimeRange localRange; <br /> readonly属性ブール監視済み <br /> readonly属性boolean temporary; <br /> }; </p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>:（2.0では変更はありません）</td> 
   <td><p>interface TimelineMarker {<br /> readonly attribute重複時間；<br /> readonly属性の重複時間；<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AdBreak {#adbreak}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreak {<br /> <br /><br /><br /> readonly attribute重複継続時間；<br /> readonly attribute adList ads;<br /><br /> <br /> readonly attribute AdInsertionType insertionType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly attribute重複時間；<br /> readonly属性重複replaceDuration;<br /><br /> readonly属性の重複時間；<br /> readonly attribute AdList adList;<br /><br /> readonly attribute DomString data;<br /><br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### 広告/AdAsset/AdClick/AdList/AdAssetList/AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>広告</strong>:interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> readonly attribute AdAssetList companionAssets;<br /><br /> readonly属性の重複時間；<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /><br /> readonly attribute unsigned short adType;<br /> readonly attribute AdInsertionType adInsertionType; <br /> <br /> readonly属性boolean clickable; <br /> readonly attribute boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> readonly attribute AdAsset primaryAsset;<br /> readonly attribute AdAssetList companionAssets;<br /><br /> readonly属性の重複時間；<br /> readonly attribute DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /><br /> readonly属性unsigned short型；<br /> readonly attribute AdInsertionType insertionType; <br /> readonly attribute object tracker;<br /><br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>:（2.0では変更はありません）</td> 
   <td><p>interface AdAsset {<br /> readonly attribute DomString id;<br /> readonly属性の重複時間；<br /> readonly attribute mediaResource resource;<br /> readonly attribute AdClick adClick;<br /> readonly attribute object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>:（2.0では変更はありません）</td> 
   <td><p>interface AdClick {<br /> readonly attribute DomString id;<br /> readonly attribute DomString title;<br /> readonly attribute DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>:（2.0では変更はありません）</td> 
   <td><p>interface AdList {<br /> readonly attribute unsigned long length;<br /> getter Ad(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>:（2.0では変更はありません）</td> 
   <td><p>interface AdAssetList {<br /> readonly attribute unsigned long length;<br /> getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>:interface AdBannerAsset:AdAsset<br /> {<br /> readonly attribute int width;<br /> readonly属性int height;<br /> readonly attribute DomString staticUrl;<br /> readonly attribute DomString height;<br /> readonly attribute DomString width;<br /> };</p> </td> 
   <td> 2.0の新機能</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakTimelineItem / AdTimelineItem {#adbreaktimelineitem-adtimelineitem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>AdBreakTimelineItem</strong>:interface AdBreakTimelineItem :TimelineItem { <br /> readonly attribute AdBreak adBreak; <br /> readonly attribute AdTimelineItemList items; <br /> }; </p> </td> 
   <td> （2.0の新機能）</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>:interface AdTimelineItem :TimelineItem { <br /> readonly attribute AdBreak adBreak; <br /> readonly attribute ad; <br /> }; </p> </td> 
   <td> （2.0の新機能）</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>:interface AdBreakTimelineItemList { <br /> readonly attribute unsigned long length; <br /> getter AdBreakTimelineItem (unsigned lo ng index); <br /> };</p> </td> 
   <td> （2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPolicy / AdBreakWatchedPolicy / AdPolicy / AdPolicyMode / AdPolicyInfo / AdPolicySelector {#adbreakpolicy-adbreakwatchedpolicy-adpolicy-adpolicymode-adpolicyinfo-adpolicyselector}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPolicy {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly attribute short AD_BREAK_POLICY_SKIP;<br /> readonly attribute short AD_BREAK_POLICY_PLAY;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE;<br /> readonly attribute short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribute short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly attribute short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly attribute short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly attribute short AD_POLICY_PLAY;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;readonly attribute short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /><br /> readonly attribute short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> readonly attribute short AD_POLICY_PLAY;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly attribute short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> readonly attribute short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> readonly attribute short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly attribute short AD_POLICY_MODE_PLAY;<br /> readonly attribute short AD_POLICY_MODE_SEEK;<br /> readonly attribute short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribute AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> readonly attribute AdTimelineItem adTimelineItem;<br /> readonly属性重複currentTime;<br /> readonly属性重複seekToTime;<br /> readonly属性の重複率；<br /> readonly属性shortモード；//AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly attribute AdBreakPlacementList adBreakPlacements <br /> ;<br /> readonly attribute ad;<br /> readonly属性重複currentTime;<br /> readonly属性重複seekToTime;<br /> readonly属性の重複率；<br /> readonly属性shortモード；//AdPolicyMode<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakCallbackFunc;<br /> /**<br /> * AdBreakTimelineItemList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallbackFunc;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallbackFunc; <br /> /**<br /> * AdBreakWatchedPolicy selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallbackFunc;<br /> };</p> </td> 
   <td><p>interface AdPolicySelector {<br /> /**<br /> * AdbreakPolicy selectPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForAdBreakFuncCallback;<br /> /**<br /> * AdBreakPlacementList selectAdBreaksToPlay(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectAdBreaksToPlayCallback;<br /> /**<br /> * AdPolicy selectPolicyForSeekIntoAd(AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectPolicyForSeekIntoAdCallback; <br /> /**<br /> * AdBreakAsWatched selectWatchedPolicyForAdBreak(<br /> * AdPolicyInfo adPolicyInfo);<br /> */<br /> attribute Object selectWatchedPolicyForAdBreakCallback;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimelineOperation {#timelineoperation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface TimelineOperation { <br /> readonly attribute Placement ; <br /> };</p> </td> 
   <td> （2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### AdBreakPlacement {#adbreakplacement}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AdBreakPlacement:TimelineOperation {<br /> readonly attribute AdBreak adBreak;<br /> readonly属性の配置；// From TimelineOperation<br /> readonly attribute重複時間；<br /> readonly属性の重複時間；<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> readonly attribute AdBreak adBreak;<br /> readonly属性の配置；<br /> readonly属性重複時間；<br /> readonly属性の重複時間；<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### AuditudeSettings {#auditudesettings}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface AuditudeSettings:AdvertisingMetadata { <br /> attribute DomString zoneId; <br /> attribute DomString mediaId; <br /> attribute DomString defaultMediaId ; <br /> attribute DomString domain ; <br /> attributeオブジェクトのターゲット設定情報； <br /> attributeオブジェクトcustomParameters ; <br /> attribute Boolean creativePackaingEnabled ;<br /> attribute Boolean showStaticBanners ;<br /> };</p> </td> 
   <td>機能は、MetadataKeys::AUDITUDE_METADATA_KEYキーによって提供されました。</td> 
  </tr> 
 </tbody> 
</table>

## 2.0のカスタマイズAPI要素の変更 {#customization-api-element-changes-for}

次の表に、バージョン1.3と2.0の間でJavaScript TVSDKのカスタマイズAPIエレメントを比較します。

このトピックの表：

* MediaPlayerItemConfig
* ContentFactory
* NetworkConfiguration

### MediaPlayerItemConfig {#mediaplayeritemconfig}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemConfig {<br /> attribute ContentFactory adFactory;<br /> attribute StringList subscribeTags;<br /><br /> attribute StringList adTags;<br /><br /> <br /> attribute AdSignalingMode adSignalingMode;<br /> attribute CustomRangeMetadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration;<br /> attribute AdvertisingMetadata advertisingMetadata;<br /> attribute Boolean useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /><br /><br /> attribute StringList adTags;<br /> attribute StringList subscribedTags;<br /> attribute MediaPlayerClientFactory clientFactory;<br /><br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### ContentFactory {#contentfactory}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interface MediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem item);<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### NetworkConfiguration {#networkconfiguration}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface NetworkConfiguration<br /> {<br /> attribute boolean forceNativeNetworking;<br /> attribute boolean useRedirectedUrl;<br /> attributeオブジェクトcookieHeader;<br /> attribute boolean readSetCookieHeader;<br /> attribute int masterUpdateInterval; <br /> attribute boolean useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>1.3では、この機能の一部はMetadataKeysによって提供されていました</td> 
  </tr> 
 </tbody> 
</table>

## 2.0のDRM API要素の変更 {#drm-api-element-changes-for}

次の表では、JavaScript TVSDKのDRM APIエレメントをバージョン1.3と2.0で比較しています。

このトピックの表：

* DRMワークフローの初期化
* DRMAcquireLicenseSettings / DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPolicy
* DRMManager

### DRMワークフローの初期化 {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>アプリケーションは、AdobePSDK.initiateDRMWorkflowを呼び出してDRMワークフローを開始する必要があります。 この呼び出しがないと、DRMビデオは再生されません。<p>interface AdobePSDK<br /> {void initiateDRMWorkFlow(<br /> DomString appStoratePath,<br /> DomString publisherId, <br /> DomString appId, DomString appVersion, <br /><br /><br /> boolean privacyModeOn);<br /> };</p> </td> 
   <td>初期化が内部的に行われ、明示的な呼び出しは必要ありませんでした。</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0 API | 1.3 API |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| 2.0では変更はありません。 | enum DRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| 2.0では変更はありません。 | enum DRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface DRMMetadata<br /> {<br /> readonly attribute DomString serverUrl;<br /> readonly attribute DomString licenseId;<br /> readonly属性は、DRMPolicyArray policies; <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPlaybackTimeWindow {#drmplaybacktimewindow}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int playbackPeriodInSeconds;<br /> readonly attribute long playbackStartDate;<br /> readonly attribute long playbackEndDate;<br /> };</p> </td> 
   <td><p>interface DRMPlaybackTimeWindow {<br /> readonly attribute int periodInSeconds;<br /> readonly attribute int startDate;<br /> readonly attribute int endDate;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicense {#drmlicense}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface DRMLicense {<br /> readonly attribute Uint8Array bytes;<br /> readonly attribute Date licenseStartDate;<br /> readonly attribute Date licenseEndDate;<br /> readonly attribute offlineStorageStartDate;<br /> readonly attribute offlineStorageEndDate; <br /> readonly attribute DomString serverUrl;<br /> readonly attribute DomString licenseID;<br /> readonly attribute DomString policyID;<br /> readonly attribute DRMPlaybackTimeWindow playbackTimeWindow;<br /> readonly attribute object customProperties;<br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMLicenseDomain {#drmlicensedomain}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authenticationDomain;<br /> readonly attribute DRMAuthenticationMethod authenticationMethod; <br /> readonly attribute DomString serverUrl;<br /> };</p> </td> 
   <td><p>interface DRMLicenseDomain {<br /> readonly attribute DomString authDomain;<br /> readonly attribute DRMAuthenticationMethod authMethod; <br /> readonly attribute DomString serverURL;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMPolicy {#drmpolicy}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribute DomString authenticationDomain;<br /> readonly attribute DRMAuthenticationMethod authenticationMethod;<br /><br /> readonly attribute DomString displayName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>interface DRMPolicy<br /> {<br /> readonly attribute DomString authDomain;<br /> readonly attribute DRMAuthenticationMethod authMethod;<br /> readonly attribute DomString dispName;<br /> readonly attribute DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMManager {#drmmanager}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DRMManager :EventTarget {<br /> void acquireLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> DRMAquireLicenseListener);<br /> void acquirePreviewLicense(DRMMetadata metadata, <br /> DRMAquireLicenseListener);<br /> void authenticate(DRMMetadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> DRMAuthenticateListener);<br /><br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, DRMErrorListener);<br /> void initialize(DRMOperationCompleteListener listener);<br /> attribute long maxOperationTime;<br /><br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener listener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener listener);<br /><br /> void resetDRM(DRMOperationCompleteListener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitImmeditely,<br /> DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> DRMMetadata metadata, <br /> DomString authenticationDomain, <br /> Uint8Array token, <br /> DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> DRMOperationCompleteListener);<br /> };</p> </td> 
   <td><p>interface DRMManager :EventTarget {<br /> void acquireLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings setting, <br /> EventContext eventContext);<br /> void acquirePreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authenticate(DRMMetadata metadata, <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString user, <br /> DomString password, <br /> EventContext eventContext);<br /><br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> attribute long maxOperationTime;<br /><br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /><br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitImmediately,<br /> EventContext eventContext);<br /> void setAuthenticationToken(<br /> DRMMetadata metadata, <br /> DomString authenticationDomain, <br /> Uint8Array token, <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> public:<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minor, <br /> const psdkutils:PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /><br /> protected:<br /> virtual ～DRMErrorListener() {}<br /> }</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>DRMMangerの非同期メソッドの1つでエラーが発生した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> public:<br /> virtual void onDRMOperationComplete() = 0;<br /><br /> protected:<br /> virtual ～DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/PSDKEvent</p> <p>DRMの初期化が完了したとき。</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/PSDKEvent</p> <p>joinLicenseDomain()アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/PSDKEvent</p> <p>leaveLicenseDomain()アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/PSDKEvent</p> <p>resetDRM()アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/PSDKEvent</p> <p>setAuthenticationTokenSet()アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMLicenseStored<p>/PSDKEvent</p> <p>storeLicenseBytes()アクションが正常に完了した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> public:<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImmutableByteArray* <br /> authenticationToken) = 0;<br /><br /> protected:<br /> virtual ～DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>DRMManager::authenticateメソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseAccatived(const DRMLicense*) = 0;<br /><br /> protected:<br /> virtual ～DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMPreviewLicenseAccatived<p>/DRMLicenseAccativedEvent</p> <p>DRMManager::acquirePreviewLicenseメソッドの呼び出しが成功した場合。</p> </li> 
     <li>kEventDRMLicenseAccatived<p>/DRMLicenseAccativedEvent</p> <p>DRMManager::acquireLicenseメソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>class DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> public:<br /> virtual void onLicenseReturnComplete(uint32_t numReturned ) = 0;<br /><br /> protected:<br /> virtual ～DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/DRMLicenseReturnCompleteEvent</p> <p>DRMManager::returnLicenseメソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 2.0向けの汎用再生API要素の変更 {#generic-playback-api-element-changes-for}

次の表に、JavaScript TVSDK 1.3と2.0の間の汎用再生APIエレメントを比較します。

このトピックの表：

* MediaResource
* MediaPlayer
* ABRControlParameters
* BufferControlParameters
* TextFormat
* MediaPlayerItemLoader

### MediaResource {#mediaresource}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaResource {<br /> attribute DomString url; <br /> attribute unsigned short type;<br /> attributeオブジェクトのメタデータ；<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribute DomString url;<br /> attribute DomString type;<br /> attributeオブジェクトのメタデータ；<br /><br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayer {#mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayer :EventTarget<br /> {<br /> void prepareToPlay(重複の位置);<br /> void play();<br /> void pause();<br /> void seek(重複の位置);<br /> void seekToLocal(重複の位置);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem item);<br /> void replaceCurrentResource(MediaResource, <br /> MediaPlayerItemConfig); <br /> void suspend();<br /> void restore();<br /> void notifyClick();<br /><br /> readonly attribute TimeRange playbackRange;<br /> readonly attribute TimeRange seekableRange;<br /> readonly属性重複currentTime;<br /> readonly属性重複localTime;<br /> readonly attribute TimeRange bufferedRange;<br /> readonly attribute DRMManager drmManager;<br /> readonly attribute MediaPlayerItem currentItem;<br /><br /> // PlayerStatus<br /><br /><br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /><br /> readonly属性unsigned short status;<br /><br /> attribute unsigned short volume;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /><br /> const unsigned short VISIBLE;//CCの表示/非表示の場合<br /> 、unsigned short INVISIBLE;//CCの表示/非表示属性の場合<br /> 、unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly attribute playbackMetrics playbackMetrics;<br /><br /> attribute重複率；<br /> attribute MediaPlayerView表示;<br /> readonly attribute timeline;<br /> attribute重複currentTimeUpdateInterval; <br /> // setting this won't be supported for 2.0<br /> };</p> </td> 
   <td><p>interface MediaPlayer :EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void seek( int position);<br /> void seekToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /><br /> <br /> <br /> <br /> <br /> <br /> readonly attribute TimeRange playbackRange;<br /> readonly attribute TimeRange seekableRange;<br /> readonly属性重複currentTime;<br /> readonly属性重複localTime;<br /> readonly attribute TimeRange bufferedRange;<br /> readonly attribute DRMManager drmManager;<br /> readonly attribute MediaPlayerItem currentItem;<br /><br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly属性unsigned short state;<br /><br /> attribute unsigned short volume;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /><br /> readonly unsigned short VISIBLE;//CCの表示に対して<br /> 、読み取り専用で、符号なしの短いINVISIBLE;//CCの表示/非表示属性の場合<br /> 、unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly attribute playbackMetrics playbackMetrics;<br /> attribute MediaPlayerConfig mediaPlayerConfig;<br /> attribute重複率；<br /> attribute MediaPlayerView表示;<br /> readonly attribute timeline;<br /><br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>（2.0の新機能）</td> 
  </tr> 
 </tbody> 
</table>

#### MediaPlayerでサポートされるイベント {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0イベント名</th> 
   <th>2.0インターフェイス</th> 
   <th> </th> 
   <th>1.3イベント名</th> 
   <th>1.3インターフェイス</th> 
  </tr> 
  <tr> 
   <td><p>（2.0から削除）</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>prepared</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdated</p> <p>メディアプレイヤーアイテムが更新されたとき。</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>更新</p> <p>メディアプレイヤーがメディアを正常に更新したとき。</p> </td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>timedMetadataAvailable</td> 
   <td>TimedMetadataEvent</td> 
   <td> </td> 
   <td>TtmedMetadata</td> 
   <td>TimedMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>timelineUpdated</td> 
   <td>イベント</td> 
   <td> </td> 
   <td>TtemlineUpdated</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>2.0で削除</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>2.0用に削除</td> 
   <td> </td> 
   <td> </td> 
   <td>playComplete</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>statusChanged</td> 
   <td>StatusEvent</td> 
   <td> </td> 
   <td>stateChanged</td> 
   <td>StateEvent</td> 
  </tr> 
  <tr> 
   <td>sizeAvailable</td> 
   <td>SizeEvent</td> 
   <td> </td> 
   <td>size</td> 
   <td>SizeEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakStarted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakStart</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adStarted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adStart</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
   <td> </td> 
   <td>adProgress</td> 
   <td>AdProgressEvent</td> 
  </tr> 
  <tr> 
   <td>adCompleted</td> 
   <td>AdEvent</td> 
   <td> </td> 
   <td>adComplete</td> 
   <td>AdEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakCompleted</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakComplete</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>timeChanged</td> 
   <td>TimeEvent</td> 
   <td> </td> 
   <td>進行状況</td> 
   <td>ProgressEvent</td> 
  </tr> 
  <tr> 
   <td>bufferingBegin</td> 
   <td>イベント</td> 
   <td> </td> 
   <td>バッファ</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>bufferingEnd</td> 
   <td>イベント</td> 
   <td> </td> 
   <td>bufferComplete</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>seekBegin</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>seekStart</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>seekEnd</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td>seekComplete</td> 
   <td>TimeEvent</td> 
  </tr> 
  <tr> 
   <td>loadInformationAvailable</td> 
   <td>LoadInformationEvent</td> 
   <td> </td> 
   <td>loadInfo</td> 
   <td>LoadInfoEvent</td> 
  </tr> 
  <tr> 
   <td>operationFailed</td> 
   <td>NotificationEvent</td> 
   <td> </td> 
   <td>operationFailed</td> 
   <td>ErrorEvent</td> 
  </tr> 
  <tr> 
   <td>drmMetadataInfoAvailable</td> 
   <td>DRMMetadataEvent</td> 
   <td> </td> 
   <td>drmMetadata</td> 
   <td>DRMMetadataEvent</td> 
  </tr> 
  <tr> 
   <td>reservationReached</td> 
   <td>ReservationEvent</td> 
   <td> </td> 
   <td>timelineHolderReached</td> 
   <td>TimelineHolderEvent</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>bitrateChanged</td> 
   <td>BitrateChangedEvent</td> 
  </tr> 
  <tr> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>rateSelected</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
   <td> </td> 
   <td>ratePlaying</td> 
   <td>PlaybackRateEvent</td> 
  </tr> 
  <tr> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
   <td> </td> 
   <td>adBreakSkipped</td> 
   <td>AdBreakEvent</td> 
  </tr> 
  <tr> 
   <td>adClicked<br /> （ユーザーが広告をクリックしたとき）。</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> ：再生プロファイルが変更されたとき。</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>seekPositionAdjusted<br /> 内部または外部のルールによってシーク位置が調整される場合。</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdated<br /> ：メディアプレイヤー項目が更新されたとき。 再生時にのみ検出可能なオーディオトラックを含む一部のストリームでは、新しいオーディオトラックが使用可能な場合に、このイベントが発生します。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captions更新 <br /> 済みメディアプレイヤー項目が更新されたとき。 ライブ/リニアストリームの場合、クライアントは、新しい使用可能なコンテンツを検出するために、メディアリソースを定期的に更新する必要があります。 この場合、メディアの特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdated <br /> メディアプレイヤー項目が更新されたとき。 ライブ/リニアストリームの場合、クライアントは、新しい使用可能なコンテンツを検出するために、メディアリソースを定期的に更新する必要があります。 この場合、メディアの特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdated<br /> ：メディアプレイヤーの項目が更新されたとき。 ライブ/リニアストリームの場合、クライアントは、新しい使用可能なコンテンツを検出するために、メディアリソースを定期的に更新する必要があります。 この場合、メディアの特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> ：時間指定イベントが生成されたときに送信されます。</td> 
   <td>TimedEvent</td> 
   <td> </td> 
   <td><p>2.0の新機能</p> </td> 
  </tr> 
 </tbody> 
</table>

### ABRControlParameters {#abrcontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /><br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>interface ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /><br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /><br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### BufferControlParameters {#buffercontrolparameters}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribute重複initialBufferTime;<br /> attribute重複playBufferTime;<br /> const重複DEFAULT_INITIAL_BUFFER_TIME;<br /> const重複DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>interface BufferControlParameters<br /> {<br /> attribute重複initialBufferTime;<br /> attribute重複playBufferTime;<br /><br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TextFormat {#textformat}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface TextFormat<br /> {<br /> // Color<br /> const unsigned short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1 ;<br /> const unsigned short COLOR_GRAY = 2 ;<br /> const unsigned short COLOR_WHITE = 3 ;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4 ;<br /> const unsigned short COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const unsigned short COLOR_BRIGHT_RED = 7 ;<br /> const unsigned short COLOR_DARK_GREEN = 8 ;<br /> const unsigned short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MEZENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> const unsigned short COLOR_BRIGHT_MEZENTA = 19 ;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /><br /> readonly attribute unsigned short fontColor;<br /> readonly attribute unsigned short backgroundColor;<br /> readonly attribute unsigned short fillColor;<br /> readonly attribute unsigned short edgeColor;<br /><br /> // Size<br /> const unsigned short SIZE_DEFAULT = 0 ;<br /> const unsigned short SIZE_SMALL = 1 ;<br /> const unsigned short SIZE_MEDIUM = 2 ;<br /> const unsigned short SIZE_LARGE = 3 ;<br /><br /> readonly属性unsigned short size;<br /><br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1 ;<br /> const unsigned short FONT_EDGE_RAISED = 2 ;<br /> const unsigned short FONT_EDGE_DEPRESSED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6 ;<br /> readonly attribute unsigned short fontEdge;<br /><br /> // Font<br /> const unsigned short FONT_DEFAULT = 0 ;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1 ;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CUSUAL = 4 ;<br /> const unsigned short FONT_CURSIVE = 5 ;<br /> const unsigned short FONT_SMALL_CAPITALS = 6 ;<br /> readonly属性unsigned shortフォント；<br /> readonly attribute unsigned short fontOpacity;<br /> readonly attribute unsigned short backgroundOpacity;<br /> readonly attribute unsigned short fillOpacity;<br /> readonly attribute unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### MediaPlayerItemLoader {#mediaplayeritemloader}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener, <br /> MediaPlayerItemConfig) ;<br /> void cancel();<br /> readonly attribute MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>2.0の新機能</td> 
  </tr> 
  <tr> 
   <td><p>interface ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>2.0の新機能</td> 
  </tr> 
 </tbody> 
</table>

## 2.0でのメディア特性API要素の変更点 {#media-characteristics-api-element-changes-for}

次の表に、C++ TVSDKのメディア特性APIエレメントをバージョン1.3と2.0で比較します。

このトピックの表：

* MediaPlayerItem
* Track、AudioTrack、ClosedCaptionsTrack
* プロファイル
* DRMMetadataInfo

### MediaPlayerItem {#mediaplayeritem}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly attribute long resourceId;<br /> readonly attribute boolean live;<br /><br /> readonly attribute boolean hasAlternateAudio;<br /> readonly attribute audioTrackList audioTracks;<br /> readonly attribute audioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack); <br /> <br /> readonly属性boolean hasClosedCaptions;<br /> readonly attribute ClosedCaptionsTrackList closedCaptionsTracks;<br /> readonly attribute ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack); <br /> <br /> readonly属性boolean hasTimedMetadata;<br /> readonly attribute timedMetadataList timedMetadata;<br /> readonly属性ブール値ダイナミック；<br /><br /> readonly attribute boolean isProtected;<br /> readonly attribute DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute profileListプロファイル;<br /> readonly attributeプロファイルselectedProfile;<br /><br /> readonly attribute boolean trickPlaySupported;<br /> readonly attribute FloatArray availablePlaybackRates;<br /> readonly attribute float selectedPlaybackRate;<br /><br /> <br /> readonly attribute MediaPlayer mediaPlayer;<br /> readonly attribute MediaPlayerItemConfig;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly attribute MediaResource resource;<br /> readonly attribute long resourceId;<br /> readonly attribute boolean live;<br /><br /> readonly attribute boolean hasAlternateAudio;<br /> readonly attribute audioTrackList audioTracks;<br /> attribute AudioTrack selectedAudioTrack;<br /><br /> <br /> readonly属性boolean hasClosedCaptions;<br /> readonly attribute ClosedCaptionsTrackList ccTracks;<br /> attribute ClosedCaptionsTrack selectedCCTrack;<br /><br /> <br /> <br /> readonly属性boolean hasTimedMetadata;<br /> readonly attribute timedMetadataList timedMetadata;<br /> readonly属性ブール値ダイナミック；<br /><br /> readonly attribute boolean isProtected;<br /> readonly attribute DRMMetadataInfoList drmMetadataInfos;<br /> readonly attribute profileListプロファイル;<br /><br /> <br /> readonly attribute boolean trickPlaySupported;<br /> readonly attribute Int32Array availablePlaybackRates;<br /><br /> readonly attribute StringList adTags;<br /><br /> readonly attribute MediaPlayer mediaPlayer;<br /><br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track/AudioTrack/ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Track<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> readonly属性boolean default;<br /> readonly属性boolean autoSelect;<br /> }; </p> </td> 
   <td>2.0の新機能</td> 
  </tr> 
  <tr> 
   <td><p>interface AudioTrack :Track<br /> {<br /> readonly attribute DomString name;//FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default;// From Track<br /> readonly attribute boolean autoSelect;//FromTrack<br /><br /> readonly attribute unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language; <br /> readonly属性boolean default;<br /> readonly属性boolean autoSelect;<br /> readonly属性booleanが強制されました。<br /><br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface AudioTrackList<br /> {<br /> readonly attribute unsigned long length;<br /> getter AudioTrack (unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface ClosedCaptionsTrack:Track<br /> {<br /> readonly attribute DomString name;//FromTrack<br /> readonly attribute DomString language;//FromTrack<br /> readonly attribute boolean default;// FromTrack<br /> readonly attribute boolean autoSelect;//FromTrack<br /><br /><br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly attribute unsigned short serviceType;<br /> readonly属性booleanが強制されました。<br /> };</p> </td> 
   <td><p>interface ClosedCaptionsTrack<br /> {<br /> readonly attribute DomString name;<br /> readonly attribute DomString language;<br /> readonly属性boolean default;<br /><br /> <br /> readonly attribute boolean active;<br /><br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface ClosedCaptionsTrackList<br /> {<br /> readonly attribute unsigned long length;<br /> getter ClosedCaptionsTrack(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### プロファイル {#profile}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>プロファイル:2.0では変更はありません。</td> 
   <td><p>interfaceプロファイル<br /> {<br /> readonly attribute unsigned int width;<br /> readonly属性unsigned int height;<br /> readonly attribute unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList:2.0では変更はありません。</td> 
   <td><p>interface ProfileList<br /> {<br /> readonly attribute unsigned long length;<br /> getterプロファイル(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DRMMetadataInfo {#drmmetadatainfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfo</strong>:2.0では変更はありません。</td> 
   <td><p>interface DRMMetadataInfo<br /> { <br /> readonly attribute DRMMetadata metadata;<br /> readonly attribute long prefetchTimestamp;<br /> readonly attribute TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>:2.0では変更はありません。</td> 
   <td><p>interface DRMMetadataInfoList<br /> {<br /> readonly attribute unsigned long length;<br /> getter DRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## C++エラーの様々な言語の例外へのマッピング {#mapping-c-errors-to-exceptions-in-different-languages}

C++エラーコードは、異なる言語の例外にマップできます。

C++ PSDKのAPIには、「スローなし」ポリシーがあります。 ほとんどのAPIメソッドは、メソッドが正常に実行されたかどうかを示すPSDKErrorCode値を返します。 非同期エラーは、エラーイベントを通じて通知されます。

ActionScriptとJAVA PSDKは、異なるポリシーを持っています。 ほとんどのエラーは、メソッドの同期部分が実行できなかったことを示すArgumentErrorまたはIllegalStateExceptionをスローします。 これらの例外はキャッチされず、アプリケーションコードが例外の処理を行います。 メソッド呼び出しが失敗した理由に関する有用な情報を、通常、これらに含めます。 例えば、prepareToPlayコマンドが無効な状態で呼び出された場合、次の例外が発生します。

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

また、ActionScript/JAVAはコンストラクタから例外をスローし、内部オブジェクトが正しく作成されなかったことを示します。 これらの例外は内部で処理され、アプリケーションに伝播されません。 例外は、アプリケーションに送信される警告通知に含まれます

例えば、受信した広告の応答に対して有効なメディアファイルが見つからない場合、有効な広告アセットオブジェクトも広告も作成できません。 その結果、タイムラインに広告が配置されず、NotificationEvent.OperationFailed通知がディスパッチされます。

Adobeビデオエンジン(AVE)と非同期で受け取るエラーコードまたは警告コードは、通常のイベントとしてアプリケーションにディスパッチされます。 通知イベントには、受け取ったすべてのエラーコードと、URL、リソース識別子、ハンドルなどの追加のメタデータが含まれます。 エラーが重大で、現在のメディアの再生を続行できない場合、MediaPlayerトランジションはERRORステータスに対するERRORコールバックと、onStatusChangedコールバックまたはMediaPlayerStatusChanged.STATUS_CHANGEDイベントをディスパッチします。 再生を続行できる場合は、通常の通知イベントがディスパッチされます。

<table> 
 <tbody> 
  <tr> 
   <th>C++エラー（PSDKErrorコード）</th> 
   <th> </th> 
   <th>Java</th> 
   <th>ActionScript</th> 
   <th>JavaScript</th> 
  </tr> 
  <tr> 
   <td>kECInvalidArgument</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>コード= 1、説明= "INVALID_ARGUMENT"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>コード= 2、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>コード= 3、説明= "ILLEGAL_STATE"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 4、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 5、説明= "CREATION_FAILED"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 5、説明= "CREATION_FAILED"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 7、説明= "DATA_NOT_AVAILABLE"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 8、説明= "SEEK_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 9、説明= "UNSUPPORTED_FEATURE"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 10、説明= "RANGE_ERROR"、およびadditionalInfo= &lt;がこの例外をスローしたメソッドによって渡された値</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 11、説明= "CODEC_NOT_SUPPORTED"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 12、説明= "MEDIA_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 13、説明= "NETWORK_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.ErrorまたはMediaPlayerNotification.Warning</td> 
   <td>MediaErrorまたはNotificationEvent</td> 
   <td>コード= 14、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 15、説明= "INVALID_SEEK_TIME"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 16、説明= "AUDIO_TRACK_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 17、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 18、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;がこの例外をスローしたメソッドによって渡された値</td> 
  </tr> 
  <tr> 
   <td>kECNotImplemented</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 19、説明= "GENERIC_ERROR"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 200、説明= "PLAYBACK_OPERATION_FAILED"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>コード= 201、説明= "NATIVE_WARNING"、およびadditionalInfo= &lt;がこの例外をスローしたメソッドによって渡されたものです</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>コード= 202、説明= "AD_RESOLVER_FAILED"、およびadditionalInfo= &lt;この例外をスローしたメソッドによって渡された値&gt;の例外</td> 
  </tr> 
 </tbody> 
</table>

## 2.0のユーティリティおよびヘルパーAPI要素の変更 {#utility-and-helper-api-element-changes-for}

次の表では、JavaScript TVSDKのUtility APIエレメントとHelper APIエレメントを、バージョン1.3と2.0の間で比較しています。

このトピックの表：

* バージョン
* TimeRange
* QOSProvider
* DeviceInformation
* LoadInfo
* 表示
* PlaybackInformation

### バージョン {#version}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly属性long major。<br /> readonly属性long minor;<br /> readonly属性long revision;<br /> readonly attribute long apiVersion;<br /> };</p> </td> 
   <td><p>interface Version<br /> {<br /> readonly attribute DomString version;<br /> readonly attribute DomString description;<br /> readonly attribute DomString major;<br /> readonly attribute DomString minor;<br /> readonly attribute DomString revision;<br /> readonly attribute DomString apiVersion;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### TimeRange {#timerange}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface TimeRange<br /> {<br /> readonly attribute unsigned long begin;<br /> readonly属性unsigned long end;<br /> readonly属性unsigned long duration;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### QOSProvider {#qosprovider}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interfaceQOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer);<br /> void detachMediaPlayer();<br /><br /> readonly attribute DeviceInformation deviceInformation;<br /> readonly attribute playbackInformation playbackInformation;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### DeviceInformation {#deviceinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /><br /> <br /> <br /> readonly attribute DomString id;<br /> readonly attribute int densityDPI;<br /> readonly attribute int heightPixels;<br /> readonly attribute int widthPixels;<br /> readonly attribute boolean seekToKeyFrame;<br /> };</p> </td> 
   <td><p>interface DeviceInformation<br /> {<br /> readonly attribute DomString os;<br /> readonly属性int sdk;<br /> readonly属性DomStringモデル；<br /> readonly属性DomString manufacturer;<br /> readonly attribute DomString id;<br /> readonly attribute int densityDPI;<br /> readonly attribute int heightPixels;<br /> readonly attribute int widthPixels;<br /><br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### LoadInfo {#loadinfo}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface LoadInfo<br /> {<br /> readonly attribute DomString url;<br /> readonly属性整数サイズ；<br /> readonly属性重複downloadDuration;<br /> readonly attribute int periodIndex;<br /> readonly属性重複mediaDuration;<br /> readonly attribute short TRACK_TYPE_FRAGMENT;<br /> readonly attribute short TRACK_TYPE_TRACK;<br /> readonly attribute short TRACK_TYPE_MANIFEST;<br /> readonly属性short型；<br /> readonly attribute DomString trackName;<br /> readonly attribute DomString trackType;<br /> readonly attribute int trackIndex;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### 表示 {#view}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0では変更はありません。</td> 
   <td><p>interface表示<br /> {<br /> readonly attribute unsigned short x;<br /> readonly属性unsigned short y;<br /> readonly属性unsigned short width;<br /> readonly属性unsigned short height;<br /><br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
  </tr> 
 </tbody> 
</table>

### PlaybackInformation {#playbackinformation}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribute timeToFirstByte;<br /> readonly属性重複timeToLoad;<br /> readonly属性重複timeToStart;<br /> readonly属性重複timeToFail;<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> readonly属性重複frameRate;<br /> readonly attribute int droppedFrameCount;<br /> readonly attribute int int percevedBandwidth;<br /> readonly属性int bitrate;<br /> readonly属性重複bufferTime;<br /> readonly attribute int bufferLength;<br /> readonly attribute int emptyBufferCount;<br /> readonly attribute bufferingTime;<br /> };</p> </td> 
   <td><p>interface PlaybackInformation<br /> {<br /> readonly attribute timeToFirstByte;<br /> readonly属性重複timeToLoad;<br /> readonly属性重複timeToStart;<br /> readonly属性重複timeToFail;<br /> readonly attribute int totalSecondsPlayed;<br /> readonly attribute int totalSecondsSpent;<br /> readonly属性重複frameRate;<br /> readonly attribute int droppedFrameCount;<br /><br /> readonly属性int bitrate;<br /> readonly属性重複bufferTime;<br /> readonly attribute int bufferLength;<br /> readonly attribute int emptyBufferCount;<br /> readonly attribute bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## 役立つリソース {#helpful-resources}

* 「 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) 」ページのヘルプドキュメントを参照してください。
