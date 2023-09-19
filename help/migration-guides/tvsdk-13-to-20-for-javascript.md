---
title: TVSDK の変換 — JavaScript 版 1.3 ～ 2.0
description: 2.0 では、多くのメソッドの署名と API 要素名が変更されました。これらの表を見て、API の変更の詳細をすべて確認します。
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '5034'
ht-degree: 0%

---

# TVSDK の変換 — JavaScript 版 1.3 ～ 2.0 {#tvsdk-conversion-to-for-javascript}

2.0 では、多くのメソッドの署名と API 要素名が変更されました。これらの表を見て、API の変更の詳細をすべて確認します。

## JavaScript でのコールバック関数の実装 {#implement-callback-functions-in-javascript}

メソッドドキュメントのコメントは、実装する必要のあるコールバックの署名を示しています。

JavaScript の場合、API 構文は Web ID に基づきます。 TVSDK インターフェイスの場合、メソッド名はと呼ばれます。 *methodName*(). アプリケーションで実装するメソッドの場合、と呼ばれる読み取り/書き込み可能な属性 *methodName* CallbackFunc がインターフェイスに追加され、アプリケーションは、メソッドを実装する関数を指すように設定する必要があります。 例：

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

## 2.0 向けの広告ワークフロー API 要素の変更 {#advertising-workflow-api-element-changes-for}

以下の表は、JavaScript TVSDK の広告ワークフロー API 要素を、バージョン 1.3 とバージョン 2.0 で比較したものです。

このトピックの表：

* TimedMetadata
* AdSignalingMode
* AdvertisingMetadata
* CustomRangeMetadata
* ReplaceTimeRange
* 配置
* 商談
* 予約
* Timeline / TimelineItem / TimelineMarker
* AdBreak
* Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset
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
   <td><p> <strong>TimedMetadata</strong>：インターフェイス TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ; <br /> const unsigned short METADATA_TYPE_ID3 = 1 ; <br /> readonly 属性 unsigned short 型； <br /> readonly 属性の長い時間。<br /> readonly 属性 DomString id;<br /> readonly 属性 DomString name;<br /> readonly 属性は、 DomString content; <br /> readonly 属性 Object metadata;<br /> }; </p> </td> 
   <td><p>interface TimedMetadata {<br /> const unsigned short METADATA_TYPE_TAG = 0 ;<br /> const unsigned short METADATA_TYPE_ID3 = 1 ;<br /> readonly 属性 unsigned short metadataType;<br /> readonly 属性の長い時間。<br /> readonly 属性 long id;<br /> readonly 属性 DomString name;<br /> <br /> readonly 属性 Object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>TimedMetadataList</strong>: （2.0 には変更はありません）</td> 
   <td><p>インターフェイス TimedMetadataList {<br /> readonly 属性 unsigned long length<br /> getter TimedMetadata(unsigned long index);<br /> };</p> </td> 
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
   <td><p>インターフェイス AdSignalingMode { <br /> const unsigned short MODE_DEFAULT, <br /> const unsigned short MODE_MANIFEST_CUES , <br /> const unsigned short MODE_SERVER_MAP , <br /> const unsigned short MODE_CUSTOM_RANGES <br /> };</p> </td> 
   <td>これにより、MetadataKeys::MANIFEST_CUES キーが置き換えられます。</td> 
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
   <td><p>AdvertisingMetadata { インターフェイス <br /> attribute AdSignalingMode モード； <br /> attribute AdBreakWatchedPolicy adBreakAsWatched; <br /> attribute boolean livePreroll; <br /> attribute boolean delayAdLoading ; <br /> };</p> </td> 
   <td>この機能は、次の URL で提供されています。<p>MetadataKeys::ADVERTISING_METADATA</p> キー。</td> 
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
   <td><p>インターフェイス CustomRangeMetadata { <br /> const unsigned short TYPE_MARK_RANGE; <br /> const unsigned short TYPE_TYPE_RANGE;DELETE符号 <br /> const unsigned short TYPE_REPLACE_RANGE; <br /> attribute unsigned short type; <br /> attribute boolean adjustSeekPosition; <br /> attribute TimeRangeList timeRangeList; <br /> };</p> </td> 
   <td>（2.0 の新機能）</td> 
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
   <td><p>interfaceReplaceTimeRange { <br /> attribute unsigned long begin; <br /> readonly 属性 unsigned long end; <br /> attribute unsigned long duration; <br /> attribute unsigned long replaceDuration; <br /> };</p> </td> 
   <td>（2.0 の新機能）</td> 
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
   <td><p>インターフェイスの配置 { <br /> const unsigned short TYPE_MID_ROLL; <br /> const unsigned short TYPE_PRE_ROLL; <br /> const unsigned short TYPE_ROLL;POST <br /> const unsigned short TYPE_SERVER_MAP; <br /> const unsigned short TYPE_CUSTOM_RANGE;<br /> readonly 属性 unsigned short 型； <br /> readonly 属性の長い時間。 <br /> readonly 属性 long duration; <br /> const unsigned short MODE_DEFAULT; <br /> const unsigned short MODE_INSERT; <br /> const unsigned short MODE_REPLACE; <br /> const unsigned short MODE_MODE;DELETE <br /> const unsigned short MODE_MARK; <br /> const unsigned short MODE_FREE_REPLACE; <br /> readonly 属性 unsigned short mode; <br /> readonly 属性 TimeRange 範囲； <br /> };</p> </td> 
   <td>（2.0 の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### 商談 {#opportunity}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>interface Opportunity { <br /> readonly 属性 DomString id; <br /> readonly 属性の配置； <br /> readonly 属性オブジェクトの設定； <br /> readonly 属性 Object customParameters; <br /> }; </p> </td> 
   <td>（2.0 の新機能）</td> 
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
   <td><p>interface reservation { <br /> readonly 属性 TimeRange 範囲； <br /> readonly 属性 long hold; <br /> }; </p> </td> 
   <td> （2.0 の新機能）</td> 
  </tr> 
 </tbody> 
</table>

### Timeline / TimelineItem / TimelineMarker {#timeline-timelineitem-timelinemarker}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p><strong>タイムライン</strong>：インターフェイスタイムライン <br /> { readonly attribute TimelineMarkerList timelineMarkers; <br /> readonly 属性 TimelineItemList timelineItems; <br /> double convertToLocalTime( double time); <br /> double convertToVirtualTime( double time); <br /> };</p> </td> 
   <td><p>interface Timeline {<br /> readonly 属性 TimelineMarkerList timelineMarkers;<br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p> <strong>TimelineItem</strong>：インターフェイス TimelineItem :<br /> TimelineMarker {<br /> readonly 属性 long id; <br /> readonly 属性 TimeRange virtualRange; <br /> readonly 属性 TimeRange localRange; <br /> readonly 属性 boolean watched; <br /> readonly 属性 boolean 一時的な； <br /> }; </p> </td> 
   <td>（2.0 の新機能）</td> 
  </tr> 
  <tr> 
   <td><strong>TimelineMarker</strong>: （2.0 には変更はありません）</td> 
   <td><p>interfaceTimelineMarker {<br /> readonly 属性 double time;<br /> readonly 属性 double duration;<br /> };</p> </td> 
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
   <td><p>interface AdBreak {<br /> <br /> <br /> <br /> readonly 属性 double duration;<br /> readonly 属性は、 AdList 広告；<br /> <br /> <br /> readonly 属性 AdInsertionType insertionType;<br /> }; </p> </td> 
   <td><p>interface AdBreak {<br /> readonly 属性 double time;<br /> readonly 属性 double replaceDuration;<br /> <br /> readonly 属性 double duration;<br /> readonly 属性 AdList adList;<br /> <br /> readonly 属性は DomString data;<br /> <br /> }; </p> </td> 
  </tr> 
 </tbody> 
</table>

### Ad / AdAsset / AdClick / AdList / AdAssetList / AdBannerAsset {#ad-adasset-adclick-adlist-adassetlist-adbannerasset}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p> <strong>広告</strong>: interface Ad {<br /> readonly 属性 AdAsset primaryAsset;<br /> readonly 属性は、 AdAssetList companionAssets;<br /> <br /> readonly 属性 double duration;<br /> readonly 属性 DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /> <br /> readonly 属性 unsigned short adType;<br /> readonly 属性 AdInsertionType adInsertionType; <br /> <br /> readonly 属性 boolean clickable; <br /> readonly 属性 boolean isCustomAdMarker;<br /> }; </p> </td> 
   <td><p>interface Ad {<br /> readonly 属性 AdAsset primaryAsset;<br /> readonly 属性は、 AdAssetList companionAssets;<br /> <br /> readonly 属性 double duration;<br /> readonly 属性 DomString id;<br /> const unsigned short ADTYPE_LINEAR = 0 ;<br /> const unsigned short ADTYPE_NONLINEAR = 1 ;<br /> <br /> readonly 属性 unsigned short 型；<br /> readonly 属性 AdInsertionType insertionType; <br /> readonly 属性オブジェクトトラッカー；<br /> <br /> <br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAsset</strong>: （2.0 には変更はありません）</td> 
   <td><p>interface AdAsset {<br /> readonly 属性 DomString id;<br /> readonly 属性 double duration;<br /> readonly 属性は、 MediaResource resource;<br /> readonly 属性 AdClick adClick;<br /> readonly 属性 Object metadata;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdClick</strong>: （2.0 には変更はありません）</td> 
   <td><p>interface AdClick {<br /> readonly 属性 DomString id;<br /> readonly 属性 DomString title;<br /> readonly 属性 DomString url;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdList</strong>: （2.0 には変更はありません）</td> 
   <td><p>interface AdList {<br /> readonly 属性 unsigned long length<br /> getter Ad(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>AdAssetList</strong>: （2.0 には変更はありません）</td> 
   <td><p>interface AdAssetList {<br /> readonly 属性 unsigned long length<br /> getter AdAsset(unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBannerAsset</strong>：インターフェイス AdBannerAsset : AdAsset<br /> {<br /> readonly 属性 int width;<br /> readonly 属性 int height;<br /> readonly 属性 DomString staticUrl;<br /> readonly 属性 DomString height;<br /> readonly 属性 DomString の幅；<br /> };</p> </td> 
   <td> 2.0 の新機能</td> 
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
   <td><p> <strong>AdBreakTimelineItem</strong>：インターフェイス AdBreakTimelineItem : TimelineItem { <br /> readonly 属性 AdBreak adBreak; <br /> readonly 属性は、 AdTimelineItemList 項目； <br /> }; </p> </td> 
   <td> （2.0 の新機能）</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdTimelineItem</strong>：インターフェイス AdTimelineItem : TimelineItem { <br /> readonly 属性 AdBreak adBreak; <br /> readonly 属性 Ad ad; <br /> }; </p> </td> 
   <td> （2.0 の新機能）</td> 
  </tr> 
  <tr> 
   <td><p><strong>AdBreakTimelineItemList</strong>：インターフェイス AdBreakTimelineItemList { <br /> readonly 属性 unsigned long length <br /> getter AdBreakTimelineItem (unsigned lo ng index); <br /> };</p> </td> 
   <td> （2.0 の新機能）</td> 
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
   <td><p>interface AdBreakPolicy {<br /> readonly 属性 short AD_BREAK_POLICY_SKIP;<br /> readonly 属性 short AD_BREAK_POLICY_PLAY;<br /> readonly 属性 short AD_BREAK_POLICY_REMOVE;<br /> readonly 属性 short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;<br /> };</p> </td> 
   <td><p> interface AdPolicyConstants {<br /> readonly 属性 short AD_BREAK_POLICY_SKIP;<br /> readonly 属性 short AD_BREAK_POLICY_PLAY;<br /> readonly 属性 short AD_BREAK_POLICY_REMOVE;<br /> readonly 属性 short AD_BREAK_POLICY_REMOVE_AFTER_PLAY;}<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p> interface AdBreakWatchedPolicy {<br /> readonly 属性 short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly 属性 short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly 属性 short AD_BREAK_AS_WATCHED_NEVER;<br /> }; </p> </td> 
   <td><p> ...<br /> readonly 属性 short AD_BREAK_AS_WATCHED_ON_BEGIN;<br /> readonly 属性 short AD_BREAK_AS_WATCHED_ON_END;<br /> readonly 属性 short AD_BREAK_AS_WATCHED_NEVER;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicy {<br /> readonly 属性 short AD_POLICY_PLAY;<br /> readonly 属性 short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly 属性 short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN; readonly 属性 short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> <br /> readonly 属性 short AD_POLICY_SKIP_AD_BREAK;<br /> };</p> </td> 
   <td><p> ... <br /> readonly 属性 short AD_POLICY_PLAY;<br /> readonly 属性 short AD_POLICY_PLAY_FROM_AD_BEGIN;<br /> readonly 属性 short AD_POLICY_PLAY_FROM_AD_BREAK_BEGIN;<br /> readonly 属性 short AD_POLICY_SKIP_TO_NEXT_AD_IN_BREAK;<br /> readonly 属性 short AD_POLICY_SKIP_AD_BREAK;<br /> ...</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyMode {<br /> readonly 属性 short AD_POLICY_MODE_PLAY;<br /> readonly 属性 short AD_POLICY_MODE_SEEK;<br /> readonly 属性 short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
   <td><p> ...<br /> {readonly 属性 short AD_POLICY_MODE_PLAY;<br /> readonly 属性 short AD_POLICY_MODE_SEEK;<br /> readonly 属性 short AD_POLICY_MODE_TRICKPLAY;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>interface AdPolicyInfo {<br /> readonly 属性 AdBreakTimelineItemList <br /> adBreakTimelineItems;<br /> readonly 属性 AdTimelineItem adTimelineItem;<br /> readonly 属性 double currentTime;<br /> readonly 属性 double seekToTime;<br /> readonly 属性の倍精度。<br /> readonly 属性 short mode; //AdPolicyMode<br /> };</p> </td> 
   <td><p>interface AdPolicyInfo {<br /> readonly 属性 AdBreakPlacementList <br /> adBreakPlacements;<br /> readonly 属性 Ad ad;<br /> readonly 属性 double currentTime;<br /> readonly 属性 double seekToTime;<br /> readonly 属性の倍精度。<br /> readonly 属性 short mode; //AdPolicyMode<br /> };</p> </td> 
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
   <td><p>interfaceTimelineOperation { <br /> readonly 属性の配置； <br /> };</p> </td> 
   <td> （2.0 の新機能）</td> 
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
   <td><p>インターフェイス AdBreakPlacement : TimelineOperation {<br /> readonly 属性 AdBreak adBreak;<br /> readonly 属性の配置； // From TimelineOperation<br /> readonly 属性 double time;<br /> readonly 属性 double duration;<br /> };</p> </td> 
   <td><p>interface AdBreakPlacement {<br /> readonly 属性 AdBreak adBreak;<br /> readonly 属性の配置；<br /> readonly 属性 double time;<br /> readonly 属性 double duration;<br /> };</p> </td> 
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
   <td><p>interface AuditudeSettings : AdvertisingMetadata { <br /> attribute DomString zoneId; <br /> attribute DomString mediaId; <br /> attribute DomString defaultMediaId ; <br /> attribute DomString ドメイン。 <br /> attribute オブジェクト targetingInfo ; <br /> attribute オブジェクト customParameters ; <br /> attribute ブール型 creativePackaingEnabled ;<br /> attribute ブール値 showStaticBanners ;<br /> };</p> </td> 
   <td>機能は、MetadataKeys::Metadata_METADATA_KEY キーによって提供されました。AUDITUDE。</td> 
  </tr> 
 </tbody> 
</table>

## 2.0 用のカスタマイズ API 要素の変更 {#customization-api-element-changes-for}

次の表は、JavaScript TVSDK のカスタマイズ API 要素を、バージョン 1.3 とバージョン 2.0 で比較したものです。

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
   <td><p>インターフェイス MediaPlayerItemConfig {<br /> attribute ContentFactory adFactory;<br /> attribute StringList subscribeTags;<br /> <br /> attribute StringList adTags;<br /> <br /> <br /> attribute AdSignalingMode adSignalingMode;<br /> attribute CustomRangeMetadata customRangeMetadata;<br /> attribute NetworkConfiguration networkConfiguration;<br /> attribute AdvertisingMetadata advertisingMetadata;<br /> attribute ブール値 useHardwareDecoder;<br /> };</p> </td> 
   <td><p>interface MediaPlayerConfig {<br /> <br /> <br /> <br /> attribute StringList adTags;<br /> attribute StringList subscribedTags;<br /> attribute MediaPlayerClientFactory clientFactory;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>interfaceContentFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem 項目 );<br /> */<br /> attribute Object retrieveAdPolicySelectorCallbackFunc;<br /> };</p> </td> 
   <td><p>interfaceMediaPlayerClientFactory {<br /> /*<br /> * AdPolicySelector retrieveAdPolicySelector(<br /> * MediaPlayerItem 項目 );<br /> */<br /> attribute Object retrieveAdPolicySelectorFunc;<br /> };</p> </td> 
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
   <td><p>インターフェイス NetworkConfiguration<br /> {<br /> attribute boolean forceNativeNetworking;<br /> attribute boolean useRedirectedUrl;<br /> attribute Object cookieHeader;<br /> attribute boolean readSetCookieHeader;<br /> attribute int masterUpdateInterval; <br /> attribute boolean useCookieHeaderForAllRequests;<br /> attribute int readLimit;<br /> };</p> </td> 
   <td>1.3 では、この機能の一部が MetadataKeys によって提供されました。</td> 
  </tr> 
 </tbody> 
</table>

## 2.0 の DRM API 要素の変更 {#drm-api-element-changes-for}

次の表は、JavaScript TVSDK の DRM API 要素を、バージョン 1.3 とバージョン 2.0 で比較したものです。

このトピックの表：

* DRM ワークフローの初期化
* DRMAcquireLicenseSettings / DRMAuthenticationMethod
* DRMMetadata
* DRMPlaybackTimeWindow
* DRMLicense
* DRMLicenseDomain
* DRMPolicy
* DRMManager

### DRM ワークフローの初期化 {#drm-workflow-initialization}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>DRM ワークフローを開始するには、アプリケーションが AdobePSDK.initiateDRMWorkflow を呼び出す必要があります。 この呼び出しがないと、DRM ビデオは再生されません。<p>インターフェイス AdobePSDK<br /> {<br /> void initiateDRMWorkFlow(<br /> DomString appStoratePath, <br /> DomString publisherId, <br /> DomString appId, <br /> DomString appVersion, <br /> boolean privacyModeOn);<br /> };</p> </td> 
   <td>初期化は内部的に行われたので、明示的な呼び出しは必要ありませんでした。</td> 
  </tr> 
 </tbody> 
</table>

### DRMAcquireLicenseSettings/DRMAuthenticationMethod {#drmacquirelicensesettings-drmauthenticationmethod}

| 2.0 API | 1.3 API |
|--- |--- |
| **DRMAcquireLicenseSettings** |  |
| 2.0 では変更はありません。 | enumDRMAcquireLicenseSettings <br>{<br> const unsigned int FORCE_REFRESH = 0;<br> const unsigned int LOCAL_ONLY = 1;<br> const unsigned int ALLOW_SERVER = 2;<br> }; |
| **DRMAuthenticationMethod** |  |
| 2.0 では変更はありません。 | enumDRMAuthenticationMethod <br>{<br> const unsigned int UNKNOWN = 0;<br> const unsigned int ANONYMOUS = 1;<br> const unsigned int USERNAME_AND_PASSWORD = 2;<br> } |

### DRMMetadata {#drmmetadata}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td>2.0 では変更はありません。</td> 
   <td><p>インターフェイス DRMMetadata<br /> {<br /> readonly 属性 DomString serverUrl;<br /> readonly 属性 DomString licenseId;<br /> readonly 属性は、DRMPolicyArray policies; <br /> };</p> </td> 
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
   <td><p>インターフェイス DRMPlaybackTimeWindow {<br /> readonly 属性 int playbackPeriodInSeconds;<br /> readonly 属性 long playbackStartDate;<br /> readonly 属性 long playbackEndDate;<br /> };</p> </td> 
   <td><p>インターフェイス DRMPlaybackTimeWindow {<br /> readonly 属性 int periodInSeconds;<br /> readonly 属性 int startDate;<br /> readonly 属性 int endDate;<br /> };</p> </td> 
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
   <td>2.0 では変更はありません。</td> 
   <td><p>interface DRMLicense {<br /> readonly 属性 Uint8Array バイト；<br /> readonly 属性 Date licenseStartDate;<br /> readonly 属性 Date licenseEndDate;<br /> readonly 属性 Date offlineStorageStartDate;<br /> readonly 属性 Date offlineStorageEndDate; <br /> readonly 属性 DomString serverUrl;<br /> readonly 属性 DomString licenseID;<br /> readonly 属性 DomString policyID;<br /> readonly 属性 DRMPlaybackTimeWindow playbackTimeWindow;<br /> readonly 属性 Object customProperties;<br /> }; </p> </td> 
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
   <td><p>interfaceDRMLicenseDomain {<br /> readonly 属性 DomString authenticationDomain;<br /> readonly 属性 DRMAuthenticationMethod authenticationMethod; <br /> readonly 属性 DomString serverUrl;<br /> };</p> </td> 
   <td><p>interfaceDRMLicenseDomain {<br /> readonly 属性 DomString authDomain;<br /> readonly 属性 DRMAuthenticationMethod authMethod; <br /> readonly 属性 DomString serverURL;<br /> };</p> </td> 
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
   <td><p>インタフェース DRMPolicy<br /> {<br /> readonly 属性 DomString authenticationDomain;<br /> readonly 属性 DRMAuthenticationMethod authenticationMethod;<br /> <br /> readonly 属性 DomString displayName;<br /> readonly 属性 DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
   <td><p>インタフェース DRMPolicy<br /> {<br /> readonly 属性 DomString authDomain;<br /> readonly 属性 DRMAuthenticationMethod authMethod;<br /> readonly 属性 DomString dispName;<br /> readonly 属性 DRMLicenseDomain licenseDomain;<br /> };</p> </td> 
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
   <td><p>インターフェイス DRMManager : EventTarget {<br /> void acquireLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings 設定， <br /> DRMAquireLicenseListener);<br /> void acquirePreviewLicense(DRMMetadata metadata, <br /> DRMAquireLicenseListener);<br /> void authenticate(DRMMetadata メタデータ， <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString ユーザー、 <br /> DomString パスワード， <br /> DRMAuthenticateListener);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, DRMErrorListener);<br /> void initialize(DRMOperationCompleteListener listener);<br /> attribute long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> DRMOperationCompleteListener);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> DRMOperationCompleteListener);<br /> <br /> void resetDRM(DRMOperationCompleteListener);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID, <br /> DomString policyID, <br /> boolean commitImmediately,<br /> DRMReturnLicenseListener);<br /> void setAuthenticationToken(<br /> DRMMetadata メタデータ， <br /> DomString authenticationDomain, <br /> Uint8Array トークン， <br /> DRMOperationCompleteListener);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> DRMOperationCompleteListener);<br /> };</p> </td> 
   <td><p>インターフェイス DRMManager : EventTarget {<br /> void acquireLicense(DRMMetadata metadata, <br /> DRMAcquireLicenseSettings 設定， <br /> EventContext eventContext);<br /> void acquirePreviewLicense(DRMMetadata metadata, <br /> EventContext eventContext);<br /> void authenticate(DRMMetadata メタデータ， <br /> DomString url,<br /> DomString &amp;authenticationDomain, <br /> DomString ユーザー、 <br /> DomString パスワード， <br /> EventContext eventContext);<br /> <br /> DRMMetadata createMetadataFromBytes(<br /> Uint8Array array, EventContext eventContext);<br /> void initialize(EventContext eventContext);<br /> attribute long maxOperationTime;<br /> <br /> void joinLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> boolean forceRefresh, <br /> EventContext eventContext);<br /> void leaveLicenseDomain(<br /> DRMLicenseDomain licenseDomain, <br /> EventContext eventContext);<br /> <br /> void resetDRM(EventContext eventContext);<br /> void returnLicense(DomString serverURL, <br /> DomString licenseID,<br /> DomString policyID, <br /> boolean commitImmediately,<br /> EventContext eventContext);<br /> void setAuthenticationToken(<br /> DRMMetadata メタデータ， <br /> DomString authenticationDomain, <br /> Uint8Array トークン， <br /> EventContext eventContext);<br /> void storeLicenseBytes(Uint8Array licenseBytes, <br /> EventContext eventContext);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>クラス DRMErrorListener : <br /> public psdkutils::PSDKInterfaceWithUserData {<br /> パブリック：<br /> virtual void onDRMError(uint32_t major, <br /> uint32_t minor, <br /> const psdkutils:: PSDKString&amp; errorString, <br /> const psdkutils::PSDKString&amp; errorServerUrl) = 0;<br /> <br /> 保護：<br /> virtual ～DRMErrorListener() {}<br /> }</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMOperationError<p>/ DRMOperationErrorEvent</p> <p>DRMManger の非同期メソッドの 1 つでエラーが発生した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>クラス DRMOperationCompleteListener : <br /> public DRMErrorListener {<br /> パブリック：<br /> virtual void onDRMOperationComplete() = 0;<br /> <br /> 保護：<br /> virtual ～DRMOperationCompleteListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMInitializationComplete<p>/PSDKEvent</p> <p>DRM の初期化が完了したとき。</p> </li> 
     <li>kEventDRMJoinLicenseDomainComplete<p>/PSDKEvent</p> <p>joinLicenseDomain() アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMLeaveLicenseDomainComplete<p>/PSDKEvent</p> <p>leaveLicenseDomain() アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMResetCompletePSDKEvent<p>/PSDKEvent</p> <p>resetDRM() アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMAuthenticationTokenSet<p>/PSDKEvent</p> <p>setAuthenticationTokenSet() アクションが正常に完了した場合。</p> </li> 
     <li>kEventDRMLicenseStored<p>/PSDKEvent</p> <p>storeLicenseBytes() アクションが正常に完了した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>クラス DRMAuthenticateListener : <br /> public DRMErrorListener {<br /> パブリック：<br /> virtual void onAuthenticationComplete(<br /> psdkutils::PSDKImutableByteArray* <br /> authenticationToken) = 0;<br /> <br /> 保護：<br /> virtual ～DRMAuthenticateListener() {}<br /> }</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMAuthenticationComplete<p>/ DRMAuthenticationCompleteEvent</p> <p>DRMManager::authenticate メソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>クラス DRMAquireLicenseListener: <br /> public DRMErrorListener {<br /> パブリック：<br /> virtual void onLicenseAcquirated(const DRMLicense*) = 0;<br /> <br /> 保護：<br /> virtual ～DRMAquireLicenseListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMPreviewLicenseAccuriated<p>/ DRMLicenseAcquiratedEvent</p> <p>DRMManager::acquirePreviewLicense メソッドの呼び出しが成功した場合。</p> </li> 
     <li>kEventDRMLicenseAccamited<p>/ DRMLicenseAcquiratedEvent</p> <p>DRMManager::acquireLicense メソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>クラス DRMReturnLicenseListener: <br /> public DRMErrorListener {<br /> パブリック：<br /> virtual void onLicenseReturnComplete(uint32_t numReturned ) = 0;<br /> <br /> 保護：<br /> virtual ～DRMReturnLicenseListener() {}<br /> };</p> </td> 
   <td>イベント/インターフェイス/説明 
    <ul> 
     <li>kEventDRMLicenseReturnComplete<p>/ DRMLicenseReturnCompleteEvent</p> <p>DRMManager::returnLicense メソッドの呼び出しが成功した場合。</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## 2.0 向けの汎用再生 API 要素の変更 {#generic-playback-api-element-changes-for}

以下の表は、JavaScript TVSDK 1.3 と 2.0 の汎用再生 API 要素を比較したものです。

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
   <td><p>interface MediaResource {<br /> attribute DomString url; <br /> attribute unsigned short type;<br /> attribute オブジェクトのメタデータ；<br /> const unsigned short TYPE_HLS;<br /> const unsigned short TYPE_HDS;<br /> const unsigned short TYPE_DASH;<br /> const unsigned short TYPE_CUSTOM;<br /> const unsigned short TYPE_UNKNOWN;<br /> };</p> </td> 
   <td><p>interface MediaResource {<br /> attribute DomString url;<br /> attribute DomString type;<br /> attribute オブジェクトのメタデータ；<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>インターフェイス MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( double position);<br /> void play();<br /> void pause();<br /> void seek( double position);<br /> void seekToLocal( double position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaPlayerItem item);<br /> void replaceCurrentResource(MediaResource rsource, <br /> MediaPlayerItemConfig config); <br /> void suspend();<br /> void restore();<br /> void notifyClick();<br /> <br /> readonly 属性 TimeRange playbackRange;<br /> readonly 属性 TimeRange seekableRange;<br /> readonly 属性 double currentTime;<br /> readonly 属性 double localTime;<br /> readonly 属性 TimeRange bufferedRange;<br /> readonly 属性 DRMManager drmManager;<br /> readonly 属性は、 MediaPlayerItem currentItem;<br /> <br /> // PlayerStatus<br /> <br /> <br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> <br /> readonly 属性 unsigned short status;<br /> <br /> attribute unsigned short volume;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> const unsigned short VISIBLE; //CC 表示用<br /> const unsigned short INVISIBLE; //CC 表示用<br /> attribute unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly 属性 PlaybackMetrics playbackMetrics;<br /> <br /> 属性倍率；<br /> attribute MediaPlayerView ビュー；<br /> readonly 属性タイムライン；<br /> attribute double currentTimeUpdateInterval; <br /> // 2.0 ではサポートされない<br /> };</p> </td> 
   <td><p>インターフェイス MediaPlayer : EventTarget<br /> {<br /> void prepareToPlay( int position);<br /> void play();<br /> void pause();<br /> void seek( int position);<br /> void seekToLocalTime( int position);<br /> void reset();<br /> void release();<br /> void replaceCurrentItem(MediaResource source);<br /> <br /> <br /> <br /> <br /> <br /> <br /> readonly 属性 TimeRange playbackRange;<br /> readonly 属性 TimeRange seekableRange;<br /> readonly 属性 double currentTime;<br /> readonly 属性 double localTime;<br /> readonly 属性 TimeRange bufferedRange;<br /> readonly 属性 DRMManager drmManager;<br /> readonly 属性は、 MediaPlayerItem currentItem;<br /> <br /> // PlayerState<br /> const unsigned short PLAYER_STATE_IDLE;<br /> const unsigned short PLAYER_STATE_INITIALIZING;<br /> const unsigned short PLAYER_STATE_INITIALIZED;<br /> const unsigned short PLAYER_STATE_PREPARING;<br /> const unsigned short PLAYER_STATE_PREPARED;<br /> const unsigned short PLAYER_STATE_PLAYING;<br /> const unsigned short PLAYER_STATE_PAUSED;<br /> const unsigned short PLAYER_STATE_SEEKING;<br /> const unsigned short PLAYER_STATE_COMPLETE;<br /> const unsigned short PLAYER_STATE_ERROR;<br /> const unsigned short PLAYER_STATE_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> readonly 属性 unsigned short state;<br /> <br /> attribute unsigned short volume;<br /> attribute ABRControlParameters abrControlParameters;<br /> attribute BufferControlParameters bufferControlParameters;<br /> <br /> readonly unsigned short VISIBLE; //CC 表示用<br /> readonly unsigned short INVISIBLE; //CC 表示用<br /> attribute unsigned short ccVisibility;<br /> attribute TextFormat ccStyle;<br /> readonly 属性 PlaybackMetrics playbackMetrics;<br /> attribute MediaPlayerConfig mediaPlayerConfig;<br /> 属性倍率；<br /> attribute MediaPlayerView ビュー；<br /> readonly 属性タイムライン；<br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>インターフェイス MediaPlayerStatus<br /> {<br /> // PlayerStatus<br /> const unsigned short PLAYER_STATUS_IDLE;<br /> const unsigned short PLAYER_STATUS_INITIALIZING;<br /> const unsigned short PLAYER_STATUS_INITIALIZED;<br /> const unsigned short PLAYER_STATUS_PREPARING;<br /> const unsigned short PLAYER_STATUS_PREPARED;<br /> const unsigned short PLAYER_STATUS_PLAYING;<br /> const unsigned short PLAYER_STATUS_PAUSED;<br /> const unsigned short PLAYER_STATUS_SEEKING;<br /> const unsigned short PLAYER_STATUS_COMPLETE;<br /> const unsigned short PLAYER_STATUS_ERROR;<br /> const unsigned short PLAYER_STATUS_RELEASED;<br /> const unsigned short PLAYER_STATUS_SUSPENDED;<br /> };</p> </td> 
   <td>（2.0 の新機能）</td> 
  </tr> 
 </tbody> 
</table>

#### MediaPlayer でサポートされるイベント {#events-supported-by-mediaplayer}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 イベント名</th> 
   <th>2.0 インターフェイス</th> 
   <th> </th> 
   <th>1.3 イベント名</th> 
   <th>1.3 インターフェイス</th> 
  </tr> 
  <tr> 
   <td><p>（2.0 で削除）</p> </td> 
   <td> </td> 
   <td> </td> 
   <td>準備済み</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td><p>itemUpdated</p> <p>メディアプレーヤーアイテムが更新されたとき。</p> </td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>更新済み</p> <p>メディアプレーヤーがメディアを正常に更新したとき。</p> </td> 
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
   <td>TtmelineUpdated</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>2.0 で削除</td> 
   <td> </td> 
   <td> </td> 
   <td>playStart</td> 
   <td>イベント</td> 
  </tr> 
  <tr> 
   <td>2.0 用に削除</td> 
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
   <td>サイズ</td> 
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
   <td>バッファー</td> 
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
   <td>adClicked<br /> ユーザーが広告をクリックしたとき。</td> 
   <td>AdClickedEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>profileChanged<br /> 再生プロファイルが変更されたとき。</td> 
   <td>ProfileEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>seekPositionAdjusted<br /> シーク位置が内部ルールまたは外部ルールによって調整される場合。</td> 
   <td>SeekEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>audioUpdated<br /> メディアプレーヤーアイテムが更新されたとき。 再生時にのみ検出可能なオーディオトラックを含む特定のストリームの場合、このイベントは、新しいオーディオトラックが使用可能になると発生します。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>captionsUpdated <br /> メディアプレーヤーアイテムが更新されたとき。 ライブ/リニアストリームの場合、クライアントは定期的にメディアリソースを更新し、新しい使用可能なコンテンツを検出する必要があります。 この場合、特定のメディア特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>masterUpdated <br /> メディアプレーヤーアイテムが更新されたとき。 ライブ/リニアストリームの場合、クライアントは定期的にメディアリソースを更新し、新しい使用可能なコンテンツを検出する必要があります。 この場合、特定のメディア特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>playbackRangeUpdated<br /> メディアプレーヤーアイテムが更新されたとき。 ライブ/リニアストリームの場合、クライアントは定期的にメディアリソースを更新し、新しい使用可能なコンテンツを検出する必要があります。 この場合、特定のメディア特性が変わる可能性があります。</td> 
   <td>MediaPlayerItemEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>timedEvent<br /> 時間指定イベントが生成された際に送信されます。</td> 
   <td>TimedEvent</td> 
   <td> </td> 
   <td><p>2.0 の新機能</p> </td> 
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
   <td><p>インターフェイス ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /> const unsigned short DEFAULT_ABR_INITIAL_BITRATE;<br /> const unsigned short DEFAULT_ABR_MIN_BITRATE;<br /> const unsigned short DEFAULT_ABR_MAX_BITRATE;<br /> const ABRPolicy DEFAULT_ABR_POLICY;<br /> };</p> </td> 
   <td><p>インターフェイス ABRControlParameters<br /> {<br /> const unsigned short ABR_POLICY_CONSERVATIVE = 0 ;<br /> const unsigned short ABR_POLICY_MODERATE = 1 ;<br /> const unsigned short ABR_POLICY_AGGRESIVE = 2 ;<br /> <br /> attribute unsigned short abrPolicy;<br /> attribute unsigned int initialBitRate;<br /> attribute unsigned int minBitRate;<br /> attribute unsigned int maxBitRate;<br /> <br /> <br /> <br /> <br /> };</p> </td> 
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
   <td><p>インタフェース BufferControlParameters<br /> {<br /> attribute double initialBufferTime;<br /> attribute double playBufferTime;<br /> const double DEFAULT_INITIAL_BUFFER_TIME;<br /> const double DEFAULT_PLAY_BUFFER_TIME;<br /> };</p> </td> 
   <td><p>インタフェース BufferControlParameters<br /> {<br /> attribute double initialBufferTime;<br /> attribute double playBufferTime;<br /> <br /> <br /> };</p> </td> 
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
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス TextFormat<br /> {<br /> //色<br /> const unsigned short COLOR_DEFAULT = 0 ;<br /> const unsigned short COLOR_BLACK = 1 ;<br /> const unsigned short COLOR_GRAY = 2 ;<br /> const unsigned short COLOR_WHITE = 3 ;<br /> const unsigned short COLOR_BRIGHT_WHITE = 4 ;<br /> const unsigned short COLOR_DARK_RED = 5 ;<br /> const unsigned short COLOR_RED = 6 ;<br /> const unsigned short COLOR_BRIGHT_RED = 7 ;<br /> const unsigned short COLOR_DARK_GREEN = 8 ;<br /> const unsigned short COLOR_GREEN = 9 ;<br /> const unsigned short COLOR_BRIGHT_GREEN = 10 ;<br /> const unsigned short COLOR_DARK_BLUE = 11 ;<br /> const unsigned short COLOR_BLUE = 12 ;<br /> const unsigned short COLOR_BRIGHT_BLUE = 13 ;<br /> const unsigned short COLOR_DARK_YELLOW = 14 ;<br /> const unsigned short COLOR_YELLOW = 15 ;<br /> const unsigned short COLOR_BRIGHT_YELLOW = 16 ;<br /> const unsigned short COLOR_DARK_MAGENTA = 17 ;<br /> const unsigned short COLOR_MAGENTA = 18 ;<br /> const unsigned short COLOR_BRIGHT_MAGENTA = 19 ;<br /> const unsigned short COLOR_DARK_CYAN = 20 ;<br /> const unsigned short COLOR_CYAN = 21 ;<br /> const unsigned short COLOR_BRIGHT_CYAN = 22 ;<br /> <br /> readonly 属性 unsigned short fontColor;<br /> readonly 属性 unsigned short backgroundColor;<br /> readonly 属性 unsigned short fillColor;<br /> readonly 属性 unsigned short edgeColor;<br /> <br /> //サイズ<br /> const unsigned short SIZE_DEFAULT = 0 ;<br /> const unsigned short SIZE_SMALL = 1 ;<br /> const unsigned short SIZE_MEDIUM = 2 ;<br /> const unsigned short SIZE_LARGE = 3 ;<br /> <br /> readonly 属性 unsigned short size;<br /> <br /> // FontEdge<br /> const unsigned short FONT_EDGE_DEFAULT = 0 ;<br /> const unsigned short FONT_EDGE_NONE = 1 ;<br /> const unsigned short FONT_EDGE_RAISED = 2 ;<br /> const unsigned short FONT_EDGE_DESPED = 3 ;<br /> const unsigned short FONT_EDGE_UNIFORM = 4 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_LEFT = 5 ;<br /> const unsigned short FONT_EDGE_DROP_SHADOW_RIGHT = 6 ;<br /> readonly 属性 unsigned short fontEdge;<br /> <br /> //フォント<br /> const unsigned short FONT_DEFAULT = 0 ;<br /> const unsigned short FONT_MONOSPACED_WITH_SERIFS = 1 ;<br /> const unsigned short FONT_PROPORTIONAL_WITH_SERIFS = 2 ;<br /> const unsigned short FONT_MONSPACED_WITHOUT_SERIFS = 3 ;<br /> const unsigned short FONT_CASUAL = 4 ;<br /> const unsigned short FONT_CURSIVE = 5 ;<br /> const unsigned short FONT_SMALL_CAPITALS = 6 ;<br /> readonly 属性 unsigned short font;<br /> readonly 属性 unsigned short fontOpacity;<br /> readonly 属性 unsigned short backgroundOpacity;<br /> readonly 属性 unsigned short fillOpacity;<br /> readonly 属性 unsigned short DEFAULT_OPACITY;<br /> };</p> </td> 
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
   <td><p>インターフェイス MediaPlayerItemLoader:<br /> {<br /> void load(MediaResource resource, long resourceId,<br /> ItemLoaderListener リスナー， <br /> MediaPlayerItemConfig config) ;<br /> void cancel();<br /> readonly 属性は、 MediaPlayerItem currentItem;<br /> };</p> </td> 
   <td>2.0 の新機能</td> 
  </tr> 
  <tr> 
   <td><p>インタフェース ItemLoaderListener<br /> {<br /> //onLoadCompleteCallbackFunc(MediaPlayerItem)<br /> var onLoadCompleteCallbackFunc;<br /> //onErrorCallbackFunc(PSDKErrorCode)<br /> var onErrorCallbackFunc;<br /> }</p> </td> 
   <td>2.0 の新機能</td> 
  </tr> 
 </tbody> 
</table>

## メディア特性 API 要素の変更（2.0 用） {#media-characteristics-api-element-changes-for}

次の表は、C++ TVSDK のメディア特性 API エレメントを、バージョン 1.3 と 2.0 で比較したものです。

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
   <td><p>interface MediaPlayerItem {<br /> readonly 属性は、 MediaResource resource;<br /> readonly 属性 long resourceId;<br /> readonly 属性 boolean live;<br /> <br /> readonly 属性 boolean hasAlternateAudio;<br /> readonly 属性は、 AudioTrackList audioTracks;<br /> readonly 属性 AudioTrack selectedAudioTrack;<br /> void selectAudioTrack(AudioTrack track); <br /> <br /> readonly 属性 boolean hasClosedCaptions;<br /> readonly 属性 ClosedCaptionsTrackList closedCaptionsTracks;<br /> readonly 属性 ClosedCaptionsTrack selectedClosedCaptionsTrack;<br /> void selectClosedCaptionsTrack(<br /> ClosedCaptionsTrack track); <br /> <br /> readonly 属性 boolean hasTimedMetadata;<br /> readonly 属性 TimedMetadataList timedMetadata;<br /> readonly 属性 boolean dynamic;<br /> <br /> readonly 属性 boolean isProtected;<br /> readonly 属性 DRMMetadataInfoList drmMetadataInfos;<br /> 読み取り専用属性 ProfileList プロファイル；<br /> readonly 属性 Profile selectedProfile;<br /> <br /> readonly 属性 boolean trickPlaySupported;<br /> readonly 属性 FloatArray availablePlaybackRates;<br /> readonly 属性 float selectedPlaybackRate;<br /> <br /> <br /> readonly 属性は、 MediaPlayer mediaPlayer;<br /> readonly 属性 MediaPlayerItemConfig;<br /> };</p> </td> 
   <td><p>interface MediaPlayerItem {<br /> readonly 属性は、 MediaResource resource;<br /> readonly 属性 long resourceId;<br /> readonly 属性 boolean live;<br /> <br /> readonly 属性 boolean hasAlternateAudio;<br /> readonly 属性は、 AudioTrackList audioTracks;<br /> attribute AudioTrack selectedAudioTrack;<br /> <br /> <br /> readonly 属性 boolean hasClosedCaptions;<br /> readonly 属性 ClosedCaptionsTrackList ccTracks;<br /> attribute ClosedCaptionsTrack selectedCCTrack;<br /> <br /> <br /> <br /> readonly 属性 boolean hasTimedMetadata;<br /> readonly 属性 TimedMetadataList timedMetadata;<br /> readonly 属性 boolean dynamic;<br /> <br /> readonly 属性 boolean isProtected;<br /> readonly 属性 DRMMetadataInfoList drmMetadataInfos;<br /> 読み取り専用属性 ProfileList プロファイル；<br /> <br /> <br /> readonly 属性 boolean trickPlaySupported;<br /> readonly 属性 Int32Array availablePlaybackRates;<br /> <br /> readonly 属性 StringList adTags;<br /> <br /> readonly 属性は、 MediaPlayer mediaPlayer;<br /> <br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

### Track / AudioTrack / ClosedCaptionsTrack {#track-audiotrack-closedcaptionstrack}

<table> 
 <tbody> 
  <tr> 
   <th>2.0 API</th> 
   <th>1.3 API</th> 
  </tr> 
  <tr> 
   <td><p>インターフェイス追跡<br /> {<br /> readonly 属性 DomString name;<br /> readonly 属性 DomString 言語；<br /> readonly 属性 boolean default;<br /> readonly 属性 boolean autoSelect;<br /> }; </p> </td> 
   <td>2.0 の新機能</td> 
  </tr> 
  <tr> 
   <td><p>インターフェイス AudioTrack : Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly 属性 DomString language;//FromTrack<br /> readonly 属性 boolean default; // From Track<br /> readonly 属性 boolean autoSelect;//FromTrack<br /> <br /> readonly 属性 unsigned int pid;<br /> };</p> </td> 
   <td><p>interface AudioTrack<br /> {<br /> readonly 属性 DomString name;<br /> readonly 属性 DomString 言語； <br /> readonly 属性 boolean default;<br /> readonly 属性 boolean autoSelect;<br /> readonly 属性 boolean 強制；<br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス AudioTrackList<br /> {<br /> readonly 属性 unsigned long length<br /> getter AudioTrack (unsigned long index);<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><p>インターフェイス ClosedCaptionsTrack : Track<br /> {<br /> readonly attribute DomString name; //FromTrack<br /> readonly 属性 DomString language;//FromTrack<br /> readonly 属性 boolean default; // FromTrack<br /> readonly 属性 boolean autoSelect;//FromTrack<br /> <br /> <br /> const unsigned short SERVICE_608_CAPTIONS = 0;<br /> const unsigned short SERVICE_708_CAPTIONS = 1;<br /> const unsigned short SERVICE_WEB_VTT_CAPTIONS = 2;<br /> readonly 属性 unsigned short serviceType;<br /> readonly 属性 boolean 強制；<br /> };</p> </td> 
   <td><p>インターフェイス ClosedCaptionsTrack<br /> {<br /> readonly 属性 DomString name;<br /> readonly 属性 DomString 言語；<br /> readonly 属性 boolean default;<br /> <br /> <br /> readonly 属性 boolean active;<br /> <br /> <br /> <br /> <br /> <br /> };</p> </td> 
  </tr> 
  <tr> 
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス ClosedCaptionsTrackList<br /> {<br /> readonly 属性 unsigned long length<br /> getter ClosedCaptionsTrack(unsigned long index);<br /> };</p> </td> 
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
   <td>プロファイル： 2.0 では変更はありません</td> 
   <td><p>インターフェイスプロファイル<br /> {<br /> readonly 属性 unsigned int width;<br /> readonly 属性 unsigned int height;<br /> readonly 属性 unsigned int bitRate;<br /> }; </p> </td> 
  </tr> 
  <tr> 
   <td>ProfileList: 2.0 に対する変更はありません</td> 
   <td><p>interfaceProfileList<br /> {<br /> readonly 属性 unsigned long length<br /> getter Profile(unsigned long index);<br /> };</p> </td> 
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
   <td><strong>DRMMetadataInfo</strong>:2.0 の変更はありません</td> 
   <td><p>インターフェイス DRMMetadataInfo<br /> { <br /> readonly 属性 DRMMetadata メタデータ；<br /> readonly 属性 long prefetchTimestamp;<br /> readonly 属性 TimeRange timeRange;<br /> };</p> </td> 
  </tr> 
  <tr> 
   <td><strong>DRMMetadataInfoList</strong>:2.0 の変更はありません</td> 
   <td><p>インターフェイス DRMMetadataInfoList<br /> {<br /> readonly 属性 unsigned long length<br /> getterDRMMetadataInfo(unsigned long index);<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## C++エラーの異なる言語での例外へのマッピング {#mapping-c-errors-to-exceptions-in-different-languages}

C++エラーコードは、異なる言語の例外にマッピングできます。

C++ PSDK の API には「ノースロー」ポリシーがあります。 ほとんどの API メソッドは、メソッドが正常に実行されたかどうかを示す PSDKErrorCode 値を返します。 非同期エラーは、エラーイベントを通じて通知されます。

ActionScriptと JAVA PSDK は、異なるポリシーを持っています。 ほとんどのエラーは、メソッドの同期部分が実行できなかったことを示す ArgumentError または IllegalStateException をスローします。 これらの例外はキャッチされず、例外の処理はアプリケーションコードが担当します。 通常は、メソッド呼び出しが失敗した理由に関する有用な情報を保持します。 例えば、prepareToPlay コマンドが無効な状態で呼び出された場合、次の例外がスローされます。

```shell
throw new IllegalStateException("Invalid player state. prepareToPlay method 
must be called only once after replaceCurrentItem or replaceCurrentResource method.");
```

また、ActionScript/JAVA は、一部の内部オブジェクトが誤って作成されたことを示すために、コンストラクタからの例外をスローします。 これらの例外は内部で処理され、アプリケーションには伝播されません。 例外は、アプリケーションに送信される警告通知に含まれます

例えば、受信した広告応答に有効なメディアファイルが見つからない場合、有効な広告アセットオブジェクトや広告を作成できません。 その結果、タイムラインに広告が配置されず、 NotificationEvent.OperationFailed 通知がディスパッチされます。

Adobeビデオエンジン (AVE) から非同期で受け取ったエラーまたは警告コードは、通常のイベントとしてアプリケーションにディスパッチされます。 通知イベントには、受け取ったすべてのエラーコードと、URL、リソース識別子、ハンドルなどの追加のメタデータが含まれます。 エラーが重大で、現在のメディアの再生を続行できない場合、 MediaPlayer は ERROR ステータスに移行し、 onStatusChanged コールバックまたは MediaPlayerStatusChanged.STATUS_CHANGED イベントがディスパッチされます。 再生が続行できる場合は、通常の通知イベントがディスパッチされます。

<table> 
 <tbody> 
  <tr> 
   <th>C++エラー（PSDKError コード）</th> 
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
   <td>コード= 1、説明= "INVALID_ARGUMENT"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNullPointer</td> 
   <td> </td> 
   <td>IllegalArgumentException</td> 
   <td>ArgumentError</td> 
   <td>コード= 2、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECIllegalState</td> 
   <td> </td> 
   <td>IllegalStateException</td> 
   <td>IllegalStateException</td> 
   <td>コード= 3、説明= "ILLEGAL_STATE"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInterfaceNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 4、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCreationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 5、説明= "CREATION_FAILED"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedOperation</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 5、説明= "CREATION_FAILED"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECDataNotAvailable</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 7、説明= "DATA_NOT_AVAILABLE"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECSeekError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>code = 8、description = "SEEK_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECUnsupportedFeature</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 9、説明= "UNSUPPORTED_FEATURE"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECRangeError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 10、説明= "RANGE_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECCodecNotSupported</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>code = 11、description = "CODEC_NOT_SUPPORTED"および additionalInfo=の例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECMediaError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 12、説明= "MEDIA_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNetworkError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 13、説明= "NETWORK_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECGenericError</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Error または MediaPlayerNotification.Warning</td> 
   <td>MediaError または NotificationEvent</td> 
   <td>コード= 14、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECInvalidSeekTime</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>code = 15、description = "INVALID_SEEK_TIME" and additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAudioTrackError</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>code = 16、description = "AUDIO_TRACK_ERROR" and additionalInfo=の例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAccessFromDifferent<p>ThreadError</p> </td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 17、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECElementNotFound</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 18、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNotImplemented</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>コード= 19、説明= "GENERIC_ERROR"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECPlaybackOperationFailed</td> 
   <td> </td> 
   <td>-</td> 
   <td>-</td> 
   <td>code = 200、description = "PLAYBACK_OPERATION_FAILED"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECNativeWarning</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>NotificationEvent</td> 
   <td>コード= 201、説明= "NATIVE_WARNING"、および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
  <tr> 
   <td>kECAdResolverFailed</td> 
   <td> </td> 
   <td>MediaPlayerNotification.Warning</td> 
   <td>-</td> 
   <td>code = 202、description = "AD_RESOLVER_FAILED"および additionalInfo=を含む例外 &lt;as passed="" by="" method="" which="" threw="" this="" exception=""&gt;</td> 
  </tr> 
 </tbody> 
</table>

## 2.0 のユーティリティおよびヘルパー API 要素の変更 {#utility-and-helper-api-element-changes-for}

次の表は、JavaScript TVSDK のユーティリティとヘルパー API の要素を、バージョン 1.3 とバージョン 2.0 で比較したものです。

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
   <td><p>インターフェイスバージョン<br /> {<br /> readonly 属性 DomString version;<br /> readonly 属性 DomString description;<br /> readonly 属性は long major;<br /> readonly 属性には、長いマイナーな属性が含まれます。<br /> readonly 属性長いリビジョン。<br /> readonly 属性 long apiVersion;<br /> };</p> </td> 
   <td><p>インターフェイスバージョン<br /> {<br /> readonly 属性 DomString version;<br /> readonly 属性 DomString description;<br /> readonly 属性 DomString major;<br /> readonly 属性 DomString minor;<br /> readonly 属性は DomString revision;<br /> readonly 属性 DomString apiVersion;<br /> };</p> </td> 
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
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス TimeRange<br /> {<br /> readonly 属性 unsigned long begin;<br /> readonly 属性 unsigned long end;<br /> readonly 属性 unsigned long duration;<br /> };</p> </td> 
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
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス QOSProvider<br /> {<br /> void attachMediaPlayer(MediaPlayer);<br /> void detachMediaPlayer();<br /> <br /> readonly 属性は、 DeviceInformation deviceInformation;<br /> readonly 属性は、 PlaybackInformation playbackInformation;<br /> };</p> </td> 
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
   <td><p>インターフェイス DeviceInformation<br /> {<br /> readonly 属性は DomString os;<br /> <br /> <br /> <br /> readonly 属性 DomString id;<br /> readonly 属性 int densityDPI;<br /> readonly 属性 int heightPixels;<br /> readonly 属性 int widthPixels;<br /> readonly 属性 boolean seekToKeyFrame;<br /> };</p> </td> 
   <td><p>インターフェイス DeviceInformation<br /> {<br /> readonly 属性は DomString os;<br /> readonly 属性 int sdk;<br /> readonly 属性 DomString モデル；<br /> readonly 属性は、DomString manufacturer;<br /> readonly 属性 DomString id;<br /> readonly 属性 int densityDPI;<br /> readonly 属性 int heightPixels;<br /> readonly 属性 int widthPixels;<br /> <br /> };</p> </td> 
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
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス LoadInfo<br /> {<br /> readonly 属性 DomString url;<br /> readonly 属性 int size;<br /> readonly 属性 double downloadDuration;<br /> readonly 属性 int periodIndex;<br /> readonly 属性 double mediaDuration;<br /> readonly 属性 short TRACK_TYPE_FRAGMENT;<br /> readonly 属性 short TRACK_TYPE_TRACK;<br /> readonly 属性 short TRACK_TYPE_MANIFEST;<br /> readonly 属性 short 型；<br /> readonly 属性 DomString trackName;<br /> readonly 属性 DomString trackType;<br /> readonly 属性 int trackIndex;<br /> };</p> </td> 
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
   <td>2.0 には変更はありません</td> 
   <td><p>インターフェイス表示<br /> {<br /> readonly 属性 unsigned short x;<br /> readonly 属性 unsigned short y と指定します。<br /> readonly 属性 unsigned short width;<br /> readonly 属性 unsigned short height;<br /> <br /> void setSize(unsigned short width, unsigned short height);<br /> void setPos(unsigned short x, unsigned short y);<br /> }</p> </td> 
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
   <td><p>インターフェイス PlaybackInformation<br /> {<br /> readonly 属性 double timeToFirstByte;<br /> readonly 属性 double timeToLoad;<br /> readonly 属性 double timeToStart;<br /> readonly 属性 double timeToFail;<br /> readonly 属性 int totalSecondsPlayed;<br /> readonly 属性 int totalSecondsSpent;<br /> readonly 属性 double frameRate;<br /> readonly 属性 int droppedFrameCount;<br /> readonly 属性 int intectedBandwidth;<br /> readonly 属性 int bitrate;<br /> readonly 属性 double bufferTime;<br /> readonly 属性 int bufferLength;<br /> readonly 属性 int emptyBufferCount;<br /> readonly 属性 double bufferingTime;<br /> };</p> </td> 
   <td><p>インターフェイス PlaybackInformation<br /> {<br /> readonly 属性 double timeToFirstByte;<br /> readonly 属性 double timeToLoad;<br /> readonly 属性 double timeToStart;<br /> readonly 属性 double timeToFail;<br /> readonly 属性 int totalSecondsPlayed;<br /> readonly 属性 int totalSecondsSpent;<br /> readonly 属性 double frameRate;<br /> readonly 属性 int droppedFrameCount;<br /> <br /> readonly 属性 int bitrate;<br /> readonly 属性 double bufferTime;<br /> readonly 属性 int bufferLength;<br /> readonly 属性 int emptyBufferCount;<br /> readonly 属性 double bufferingTime;<br /> };</p> </td> 
  </tr> 
 </tbody> 
</table>

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。
