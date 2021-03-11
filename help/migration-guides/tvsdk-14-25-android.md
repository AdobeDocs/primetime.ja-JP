---
title: Android向けTVSDK 1.4 ～ 2.5(Java)
description: TVSDK 2.5では、パフォーマンス、セキュリティ、統合の向上などの点で、バージョン1.4と比べて複数のメリットがオファーされます。
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
translation-type: tm+mt
source-git-commit: b33240bf1b42b80389cd95a7ae4d3f85185a2d32
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---


# Android向けTVSDK 1.4 ～ 2.5 (Java) {#tvsdk-to-for-android-java}

TVSDK 2.5では、パフォーマンス、セキュリティ、統合の向上などの点で、バージョン1.4と比べて複数のメリットがオファーされます。

TVSDKは、最も重要なデバイス上の最も大きな課題を解決します。 Androidは、市場シェアの86%以上を占め、世界的な優位性を維持しています。 Android上のTVSDKへの移行により、再生パフォーマンスが最適化され、新しいコンテンツ形式がサポートされ、ユーザーのエンゲージメントが向上し、市場投入時間が短縮されます。

## TVSDK v2.5 {#benefits-of-migrating-to-tvsdk-v}への移行の利点

TVSDK 2.5では、パフォーマンス、セキュリティ、統合の向上などの点で、バージョン1.4と比べて複数のメリットがオファーされます。 この新しいバージョンに移行する利点を簡単に理解するために、以下を参照してください。

サードパーティのベンチマーク調査によると、v2.5では、業界平均で、起動時間が5倍に短縮され、ドロップフレームが3.8倍に短縮されました。

| パフォーマンスの機能 | 説明 |
|--- |--- |
| VODおよびLiveの即時オン | チャネルの切り替え時に、VODおよびライブリニアストリームの即時再生用に、TVのようなエクスペリエンスのために、初期tsセグメントを事前読み込みします。 |
| 遅延広告読み込み | パラレルスレッドでのミッドロール広告の解決中に、プリロールまたはコンテンツが利用可能になるとすぐに開始が再生されます。 |
| 永続的なネットワーク接続 | ネットワークコードの効率が向上し、遅延が減少し、再生パフォーマンスが向上します。 |
| ABRロジックの改善 | 新しいABRロジックは、バッファー長、バッファー長の変化率、測定された帯域幅に基づいています。 これにより、ABRは帯域幅が変動する場合に適切なビットレートを選択し、バッファー長が変化するレートを監視することで、ビットレートの切り替えが実際に発生する回数を最適化します。 |
| 部分的なセグメントのダウンロード | セグメントから十分なフレームが得られるとすぐに開始が再生され、ビデオがクライアント側で確実にレンダリングされます。 |
| 並行ダウンロード | TVSDKは、圧縮解除されたコンテンツを再生パフォーマンスを最適化するために、オーディオおよびビデオのセグメントを並行してダウンロードします。 |

再生機能は、デジタルでリニア放送を行うことで消費者の関与性を向上させます。 また、WidevineなどのネイティブDRMをHD再生に活用するのにも役立ちます。

| 再生機能 | 説明 |
|--- |--- |
| MP4再生 | MP4の短いクリップは、TVSDK内の再生に再トランスコードする必要はありません。 |
| DASH VODコンテンツの再生 | 基本的なDASH VOD再生の使用例がサポートされています。 |
| ABRを使用したスムーズなトリック再生 | 低速のキーフレームと高速のI-Frameを使用するHLSでの早送りと巻き戻しのサポート。 ABRは、サポートされるすべてのフレームをサポートします。 |

これらの機能は、ネイティブDRMを使用したHD再生など、Studioの制限を満たすのに重要です。

| 機能 | 説明 |
|--- |--- |
| 解像度ベースの出力保護 | 再生は、DRM要件で許可される特定の解像度にのみ制限できます。 Primetime DRMを通じてのみ使用できます。 |
| Widevineのサポート | ネイティブDRMの使用例を有効にするために、DASH VODストリームでサポートされます。 |

直接請求の機能強化は、毎月請求用の手動レポートを作成する必要がなくなります。 VHL 2.0では、ビルド前の統合とトラッキングの精度を向上させることで、市場投入時間を短縮できます。

| 機能 | 説明 |
|--- |--- |
| 堀の統合 | Morthからの広告視聴率測定のサポート。 |
| VHL 2.0 | 最新の最適化されたビデオハートビートライブラリ統合。Adobe Analyticsの使用データの自動収集に使用されます。 |
| フェイルオーバーのサポート | ホストサーバー、プレイリストファイルおよびセグメントに障害が発生した場合でも、再生を中断せずに続行するために実装された追加の戦略です。 |
| 直接請求の統合 | 顧客が使用するストリームに関してAdobe Primetimeが認証した請求指標をAdobe Analyticsバックエンドに送信します。 |

>[!NOTE]
>
>TVSDK v1.4のすべての機能は、マルチCDNのサポートを除き、v2.5でサポートされます。

## 移行プロセスの概要{#overview-of-the-migration-process}

TVSDK 1.4から2.5へのスムーズな移行では、バージョン2.5ライブラリに変更し、リコンパイルしてから、このドキュメントを使用して発生する問題のデバッグを行います。

TVSDK v1.4ライブラリは、v2.5ライブラリとは連携せず、共存しません。 TVSDK 2.5でv2.5ライブラリを使用し、アプリケーションと統合を移行してTVSDK 2.5にアップグレードする必要があります。このドキュメントでは、アプリケーションコードの変更方法と変更内容、および再コンパイル中のエラーに対処する方法を説明します。

psdk.jarファイルは、様々な機能をサポートするためにサードパーティライブラリを使用します。 ライブラリを削除しないようにするには、`proguard.cfg`ファイルに次の内容を含めます。

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

`build.gradle`ファイルには、TVSDKベースのJARファイルを含めるためのコンパイルディレクティブを含める必要があります。 アプリにAdobeビデオ分析が含まれる場合は、Adobeビデオ分析の統合に必要な追加のjarに対して、コンパイルディレクティブをアプリに含める必要があります

```java
# Compile Adobe TVSDK jars compile files('libs/psdk-va.jar')
compile files('libs/VideoHeartbeat.jar')
```

このドキュメントでは、複数のマイナーな変更については説明しません。 APIのマイナーな変更については、[Android用TVSDK 2.5 API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/index.html)を参照してください。 対応するC++ APIリファレンスに詳しい説明が記載されています。 類似のC++ APIドキュメントについては、[Android用TVSDK 2.5 API](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.5/index.html)を参照してください。

APIの使用例は、TVSDKで配布されるリファレンス実装で複数説明されています。

## TVSDK v2.5 {#api-changes-in-tvsdk-v}でのAPIの変更

新しいAPI、古いAPI、変更されたAPIは、以下にドキュメント化されています。

| TVSDK v1.4 | TVSDK v2.5 | 説明 |
|--- |--- |--- |
| com.adobe.ave.drm .DRMAcquireLicenseSettingsを読み込む | import com.adobe.mediacore.drm .DRMAcquireLicenseSettings; | TVSDK 2.5 APIのすべてのクラス名は、com.adobe.mediacoreプレフィックスで始まります。 これは一例にすぎません。 |
| MediaPlayerException、IllegalStateExceptionまたはIllegalArgumentException | MediaPlayerException | 2.5では、APIはMediaPlayerExceptionのみを生成します。 |
| MediaPlayer.PlayerState(MediaPlayer.イベント.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | v2.5では、MediaPlayer.PlayerStateは、別の列挙MediaPlayerStatusに名前が変更されました。 |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext(); | オブジェクトの作成に使用する静的メソッドは、パブリックコンストラクタで置き換えられます。 |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | MediaPlayer.seekToLocalTime()メソッドは、現在はMediaPlayer.seekToLocal()と呼ばれています。 |
| closedCaptionsTrack.isActive() |  | 使用不可 |
| MetadataNode | メタデータ | v2.5では、Metadataクラスがv1.4 MetadataNodeクラスの使用を置き換えます。 |
| DefaultMetadataKeys | MetadataKeys | v1.4のDefaultMetadataKeysはv2.5 enum MetadataKeysにあります。 |
| AdvertisingFactory | ContentFactory | v1.4のAdvertisingFactoryの名前がv2.5でContentFactoryに変更されました。 |
| PlacementOpportunityDetector | OpportunityGenerator | ディテクターはジェネレーターに置き換えられます。 |
| mediaPlayer.getView().notifyClick(); | mediaPlayer.notifyClick(); | MediaPlayerViewのnotifyClick()メソッドは、MediaPlayerクラスに移動されました。 |
| public ABRControlParameters(ABRPolicy abrPolicy, int nInitialBitRate, int nMinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int nMinBitRate, int nMaxBitRate, ABRPolicyAbrPolicy, int nMinTrickPlayBitRate, int nMaxTrickPlayBitRatRate, intIntNmaxTrickPlayBandwidthUsage、重複dMaxPlayoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | 使用不可 |
|  | playbackInformation.get AncevedBandwidth() | TVSDK v2.5 QOSProviderには、ストリーミングセッション中に認識される帯域幅を決定する新しいプロパティがあります。 |

### 削除されたクラス{#removed-classes}

次のクラスは削除され、同等のものはありません。

* `TimeRangeCollection`
* `PSDKConfig`
* `BaseLogger`
* `DefaultLogger`
* `Log`
* `Logger`
* `LogFactory`
* `NullLogger`

これらのクラスの最後の6つは、リファレンス実装でユーティリティクラスとして使用できます。

## 名前空間変更{#namespace-changes}

TVSDK 2.5 APIは、名前空間を統合しました。

TVSDK 2.5 APIのすべてのクラス名は、com.adobe.mediacoreプレフィックスで始まります。 TVSDK 1.4 API開始の一部のクラス名とcom.adobe.ave. 対応する2.5クラスは、com.adobe.aveをcom.adobe.mediacoreに変更します。 例えば、1.4および2.5のコードの次の行の変更点に注意してください。

```java
// TVSDK 1.4
import com.adobe.ave.drm.DRMAcquireLicenseSettings; import com.adobe.ave.drm.DRMLicense;
import com.adobe.ave.drm.DRMManager; import com.adobe.ave.drm.DRMMetadata
```

```java
// TVSDK 2.5
import com.adobe.mediacore.drm.DRMAcquireLicenseSettings; import com.adobe.mediacore.drm.DRMLicense;
import com.adobe.mediacore.drm.DRMManager; import com.adobe.mediacore.drm.DRMMetadata;
```

## イベント処理の変更{#changes-in-event-handling}

このバージョンでイベントを登録するには、ハンドラを`addEventListener`に渡します。 イベントのリストは、バージョン1.4からバージョン2.5に大幅に変更されました。\
例えば、`MediaPlayerEvent.STATUS_CHANGED:`のイベントハンドラを登録する方法を次に示します。

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

次に、イベントが1.4で登録された方法を示します。

```java
mPlayer.addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {
@Override
public void onStateChanged(MediaPlayer.PlayerState state,
MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});
```

MediaPlayerEvent列挙には、すべてのイベントコードが含まれています。 2.5では、1.4の次のイベントコードは存在しなくなりました。

* `ADBREAK_PLACEMENT_COMPLETED`
* `ADBREAK_PLACEMENT_FAILED`
* `ADBREAK_REMOVAL_COMPLETED`
* `AD_BREAK_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_COMPLETE`
* `AD_MANIFEST_LOAD_FAILED`
* `AUDIO_TRACK_FAILED`
* `BACKGROUND_MANIFEST_FAILED`
* `BUFFERING_FULL, CUSTOM_AD_EVENT`
* `CONTENT_MARKER`
* `CONTENT_PLACEMENT_COMPLETE`
* `CONTENT_CHANGED`
* `ITEM_REPLACED`
* `ITEM_READY`
* `VIEW_CLICKED`
* `PREPARED`
* `UPDATED`
* `OPPORTUNITY_COMPLETED`
* `OPPORTUNITY_CREATED`
* `OPPORTUNITY_FAILED`
* `PAUSE_AT_PERIOD_END`
* `PLAYBACK_STARTED`
* `PLAYBACK_PAUSED`
* `PLAYBACK_COMPLETED`
* `PLAY_COMPLETE`
* `POST_ROLL_COMPLETE`
* `RESOURCE_LOADED`
* `TIMED_METADATA_SKIPPED`
* `VIDEO_ERROR`
* `VIDEO_STATE_CHANGED`

2.5で新たに追加されたイベントコードを次に示します。

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### イベント名を変更{#renamed-events}

| 新しい名前 | 古い名前 |
|--- |--- |
| SEEK_BEGIN | SEEK_STARTED |
| SEEK_END | SEEK_COMPLETED |
| SEEK_POSITION_ADJUSTED | SEEK_ADJUST_COMPLETED |
| BUFFERING_BEGIN | BUFFERING_STARTED |
| BUFFERING_END | BUFFERING_COMPLETED |
| AUDIO_TRACK_UPDATED | AUDIO_TRACK_CHANGED |
| STATUS_CHANGED | STATE_CHANGED |
| TIMED_METADATA_AVAILABLE | TIMED_METADATA_ADDED |
| SIZE_AVAILABLE | SIZE_CHANGED |
| LOAD_INFO | LOAD_INFORMATION_AVAILABLE |

## MediaPlayerの変更{#mediaplayer-changes}

`MediaPlayer`を構築する新しい方法と、いくつかの方法に変更が加えられました。

**MediaPlayerクラスの変更**

`MediaPlayer`クラスの変更点を次に示します。

* `MediaPlayerStatus`列挙は`MediaPlayer.PlayerState`を置き換えます。 例：

```java
//TVSDK v1.4
mPlayer. addEventListener(MediaPlayer.Event.PLAYBACK, new MediaPlayer.PlaybackEventListener() {

@Override
public void onStateChanged(MediaPlayer.PlayerState state,MediaPlayerNotification notification) {
//Handle status change event
}
// Additional handlers
...
});

//TVSDK v2.5
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED, new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
//Additional handlers.
...
});
```

* `MediaPlayer.seekToLocalTime()`メソッドは、現在は`MediaPlayer.seekToLocal`と呼ばれています。 例：

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* `MediaPlayerView.notifyClick()`メソッドは、現在は`MediaPlayer.notifyClick()`です。 例：

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* 以前の`MediaPlayer.MediaPlayer.getNotificationHistory()`メソッドは、現在は削除され、置き換えられません。
* 前者の`MediaPlayer.replaceCurrentItem()`は、次の2つの方法に分かれます。`replaceCurrentResource()`は`MediaResource`のインスタンスを取り、`MediaPlayerItem`のインスタンスを取ります。`replaceCurrentItem()`はのインスタンスを取ります。 例：

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());

mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5 - replacing a resource
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());
...
try {
mMediaPlayer.replaceCurrentResource(playerResource, _mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
// TVSDK 2.5 - replacing an Item
MediaPlayerItemLoader itemLoader = new MediaPlayerItemLoader(context, new MediaPlayerItemLoader.LoaderListener() {

@Override
public void onError(PSDKErrorCode psdkErrorCode, String s) {
...
}
@Override
public void onLoadComplete(MediaPlayerItem mediaPlayerItem) {
...
}
@Override
public void onBufferingBegin() {
...
}
@Override
public void onBufferPrepared() {
...
}
});
MediaResource playerResource = new MediaResource(url,
MediaResource.Type.HLS, getAdvertisingMetadata());

itemLoader.load(playerResource); itemLoader.prepareBuffer();
mediaPlayer.replaceCurrentItem(itemLoader.getItem());
```

これを使用して、ブラックアウトの場合と同様に、初期化済みのMediaPlayerインスタンスを切り替えることができます。

**コンストラクタは、静的create()メソッドを置き換えます**

TVSDK v1.4の`create()`メソッドを使用する代わりに、TVSDK v2.5でコンストラクターを使用できます。Defaultで始まる名前を持つすべてのクラス（`DefaultMediaPlayer`、`DefaultNetworkConfig`、`DefaultContentFactory`など）は、v2.5では使用できません。

TVSDK v1.4 APIがクラスの作成に次のパターンを使用する場合があります。

1. インターフェイスを定義します（例：`MediaPlayer`）。
1. デフォルトのクラスを指定します（例：`DefaultMediaPlayer`）。
1. インターフェイスを実装するクラスを提供するデフォルトクラスに`create()`メソッドを提供します。

TVSDK v2.5では、このようなインターフェイスは具体的なクラスで、それぞれのコンストラクターを使用してこれらのクラスのインスタンスを作成します。 次のコードスニペットに、この違いを示します。

```java
//TVSDK v1.4
// Create a media player
// MediaPlayer is an interface
private MediaPlayer createMediaPlayer() { MediaPlayer mediaPlayer =
DefaultMediaPlayer.create(getActivity().getApplicationContext()); return mediaPlayer;

//TVSDK v2.5
// Create a media player
// MediaPlayer is a class that you instantiate private MediaPlayer createMediaPlayer() {
MediaPlayer mediaPlayer =
new MediaPlayer(getActivity().getApplicationContext()); return mediaPlayer;
}
```

このパターンに従わないが、1.4で`create()`メソッドを使用する他のクラスは次のとおりです。

* MediaResource\
   これは以前は`MediaResource.createFromUrl()`を使っていました。 次に、URL、リソースタイプおよびメタデータを取るコンストラクタを使用します。 例：

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, getAdvertisingMetadata());
mediaPlayer.replaceCurrentItem(playerResource);

//TVSDK v2.5
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, getAdvertisingMetadata());

try { mediaPlayer.replaceCurrentResource(playerResource,_mediaPlayerItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
// handle exception.
}
```

* 広告
* AdAsset
* AdBreak

一部のクラス（例えば、`ContentFactory`）は抽象クラスで、パブリックに使用可能なデフォルトの実装がありません（例えば、`DefaultContentFactory`）。 このような場合は、次のように便利な関数を使用してデフォルトの実装を指定できます。`mediaPlayerItemConfig.getDefaultContentFactory()`

**クローズドキャプションの変更**

次の変更は、クローズドキャプションに関連するクラスに影響します。

* クローズドキャプショントラックを取得する場合、`MediaPlayerItem.getClosedCaptionTracks()`はアクティブなトラックのみを返します。
* `ClosedCaptionTrack` の `isActive()` メソッドがなくなりました。

```java
//TVSDK v1.4
public List<String> getClosedCaptionTracks(String label) {
List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks(); Iterator<ClosedCaptionsTrack> iterator =
closedCaptionsTracks.iterator();
if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); String isActive = closedCaptionsTrack.isActive() ? " (" + label
+ ")" : "";
closedCaptionsTracksAsStrings.add(closedCaptionsTrack.getName()
+ " : " + closedCaptionsTrack.getLanguage() + isActive);
}
}
return closedCaptionsTracksAsStrings;
}

//TVSDK v2.5
public List<String> getClosedCaptionTracks(String label) {

MediaPlayerItem currentItem = mediaPlayer.getCurrentItem(); List<ClosedCaptionsTrack> closedCaptionsTracks =
currentItem.getClosedCaptionsTracks();
Iterator<ClosedCaptionsTrack> iterator = closedCaptionsTracks.iterator();

List<String> closedCaptionsTracksAsStrings = new ArrayList<String>(); if (currentItem != null) {
while (iterator.hasNext()) {
ClosedCaptionsTrack closedCaptionsTrack = iterator.next(); closedCaptionsTracksAsStrings.
add(closedCaptionsTrack.getName() + " : ");
}
}
return closedCaptionsTracksAsStrings;
}
// Add snippet and desc for CaptionsUpdatedEventListener mediaPlayer.addEventListener(MediaPlayerEvent.CAPTIONS_UPDATED,
captionsUpdatedEventListener);

private final CaptionsUpdatedEventListener captionsUpdatedEventListener = new CaptionsUpdatedEventListener() {

@Override
public void onCaptionsUpdated(MediaPlayerItemEvent mediaPlayerItemEvent) { getActivity().findViewById(R.id.sbPlayerControlCC).setVisibility(
View.VISIBLE/*Visible*/);
}
};
```

## 広告の変更{#advertising-changes}

バージョン2.5では、広告関連の変更がいくつかあります。

**広告行動の変更**

ユーザーが広告ポッドを超えるシークを実行した場合の広告再生のデフォルトの動作は、v2.5では若干変わります。広告の時間が視聴されない場合、広告はシークフォワード後に再生されます。 アプリがデフォルトの広告ポリシーを使用している場合、広告の時間は再生の完了後に削除されます。 TVSDK v2.5を使用して、ユーザーがタイムライン上の広告ポッドの背後をシークし、広告の時間が視聴されない場合、広告は再生されません。

ただし、TVSDK v1.4では、デフォルトで、後方へシークした場合に広告が再生されます。 例えば、3番目と4番目の広告の時間の間を逆方向にシークする場合、TVSDK v1.4のデフォルトの動作では、3番目の広告の時間が再生されます。

**広告ルールの変更**

広告ルールはJSONファイルを使用して指定されます。 JSONファイルの形式は、TVSDKの両方のバージョンで同じままです。 ただし、TVSDK v2.5では、広告ルールのJSONファイルは、HTTP URLを介してアクセス可能な場所でホストする必要があります。 アプリケーションは、AuditudeSettingsのインスタンスを使用できます。

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

TVSDKバージョン1.4では、このファイルはアプリケーション内のassetsフォルダーの下に配置され、TVSDKがファイルを読み込みます。

**広告ファクトリ名の変更**

`AdvertisingFactory` の名前が付けられま `ContentFactory`す。`ContentFactory`を使うと、カスタマイズした広告ワークフローを作成する際に、そのメソッドの一部を無効にすることができます。 次のように、デフォルトの動作を維持するには、return nullを使用します。

```java
//TVSDK v2.5
new ContentFactory() {
@Override
public AdPolicySelector retrieveAdPolicySelector(MediaPlayerItem item) { return new CustomAdPolicySelector();
}
@Override
public List<OpportunityGenerator> retrieveGenerators(MediaPlayerItem item) { return null;
}
@Override
public List<ContentResolver> retrieveResolvers(MediaPlayerItem item) { return null;
}
@Override
public List<CustomAdHandler> retrieveCustomAdPlaybackHandlers(MediaPlayerItem item) { return null;
}
};
```

**長さ0の広告の時間**

広告サーバーが広告を返さない場合、TVSDK 2.5は、長さ0の広告の時間をプレースホルダーとして挿入します。

長さが0の広告の時間は、onAdBreakStartedイベントを使用して広告の時間内で0になる広告の数を検出することで判断でき、アプリケーションはそれに応じてこれらの広告の時間を処理する必要があります。

**メタデータの変更**

Metadataクラスは、以前のMetadataNodeクラスに対して、より有効な置き換えを提供します。

* Metadataクラスには、文字列、バイト配列、およびその他のMetadataオブジェクトを格納できます。

```java
TVSDK v1.4
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new MetadataNode();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingParameters(advertisingParams);

return adSettings;
}
//TVSDK v2.5
public AuditudeSettings createAdvertisementSettings() { Metadata advertisingParams = new Metadata();
advertisingParams.setValue("platform", Build.VERSION.RELEASE); advertisingParams.setValue("model", Build.MODEL);
AuditudeSettings adSettings = new AuditudeSettings();
// Set ad domain, zone id and media_id
...

// Set the target paramaters adSettings.setTargetingInfo(advertisingParams);

return adSettings;
}
```

* `MetadataKeys`列挙は`DefaultMetadataKeys`を置き換えます。 `DefaultMetadataKeys`内のすべてのキーが新しいバージョンに存在するわけではありません。

```java
//TVSDK v1.4
if (this.mediaPlayer != null && this.mediaPlayer.getCurrentItem() != null) { MetadataNode resourceMetadata =
(MetadataNode) this.mediaPlayer.getCurrentItem().getResource().getMetadata();
VideoAnalyticsMetadata vaMetadata = (VideoAnalyticsMetadata)
resourceMetadata.getNode(DefaultMetadataKeys.
VIDEO_ANALYTICS_METADATA_KEY.getValue());
}

//TVSDK v2.5
if (resourceMetadata.containsKey(VideoAnalyticsMetadata.
VIDEO_ANALYTICS_METADATA_KEY)) {
JSONObject vaMetadataObj =
new JSONObject(resourceMetadata.
getValue(VideoAnalyticsMetadata. VIDEO_ANALYTICS_METADATA_KEY));
vaMetadata = parseVideoAnalyticsMetadata(vaMetadataObj);
}

} catch (JSONException e) { e.printStackTrace();
}
```

* 広告メタデータは、現在は、Metadataのサブクラスである`AdvertisingMetadata`クラスで表され、`MediaResource`ではなく`MediaPlayerItemConfig`に保存されます。

```java
//TVSDK v1.4
MetadataNode mediaMetadata = new MetadataNode();

if (stream.live) { mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(),
getAdSettingsForLive());
} else {
mediaMetadata.setNode(DefaultMetadataKeys.AUDITUDE_METADATA_KEY.getValue(), getAdSettingsForVod());
}
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

if (stream.live) {
AuditudeSettings adSettings = getAdSettingsForLive(); adSettings.setLivePreroll(true); mediaItemConfig.setAdvertisingMetadata(adSettings);
} else {
// Set the advertising parameters for VOD. mediaItemConfig.setAdvertisingMetadata(getAuditudeSettingsForVod());
}

// Create advertising metadata node Metadata mediaMetadata = new Metadata();

// Asset Url
MediaResource playerResource =
new MediaResource(url, MediaResource.Type.HLS, mediaMetadata);
try {
mediaPlayer.replaceCurrentResource(playerResource, mItemConfig);
} catch (MediaPlayerException mediaPlayerException) {
//handle exception.
}
```

ネットワーク構成メタデータ(以前は`MediaResource`クラスのメンバーであり、現在は`NetworkConfiguration`クラスで表され、`MediaResource`ではなく`MediaPlayerItemConfig`に格納されています。

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**TimedMetadata解析の変更**

`TimedMetadata`の解析は、ID3タグを解析するためのデータ型に関して2.5で変更されました。

```java
//TVSDK v1.4
public void onTimedMetadata(TimedMetadata timedMetadata) { TimedMetadata.Type type = timedMetadata.getType();
if (type.equals(TimedMetadata.Type.ID3)){ PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata(); Set<String> keys = metadata.keySet();
for (String key : keys) {
String value = metadata.getValue(key); PMPDemoApp.logger.i(LOG_TAG + "#onTimedMetadata",
"Key = " + key + " Value = " + value);
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { parseSCTE35Tag(timedMetadata);
}
}
}

//TVSDK v2.5
public void onTimedMetadata(TimedMetadataEvent timedMetadataEvent) { PMPDemoApp.logger.i(LOG_TAG + " inside"," ontimedmetadata"); TimedMetadata timedMetadata = timedMetadataEvent.getTimedMetadata();

TimedMetadata.Type type = timedMetadata.getType(); if (type.equals(TimedMetadata.Type.ID3)) {
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New ID3 tag detected at time = " + timedMetadata.getTime());
Metadata metadata = timedMetadata.getMetadata();
if (metadata != null) { PMPDemoApp.logger.i(LOG_TAG +
"::expandID3Metadata", "isEmpty " + metadata.isEmpty());
Set<String> keys = metadata.keySet(); PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"No of keys=" + keys.size());
String s;
for (String key : keys) {
byte[] value = metadata.getByteArray(key); s = new String(value);
if (key.equalsIgnoreCase("APIC"))
s = "SUPPRESSING BINARY DATA FOR ATTACHED PICTURE.";
PMPDemoApp.logger.i(LOG_TAG + "::expandID3Metadata",
"Key=" + key + ", Length=" + value.length + ", Value=" + s.trim());
}
}
} else if (_mediaPlayer.getPlaybackRange() != null &&
_mediaPlayer.getPlaybackRange().getDuration() > 0) { displayRanges();
PMPDemoApp.logger.i(LOG_TAG +
"#onTimedMetadata",
"New timed metadata. Name " + timedMetadata.getName() +
", time " + timedMetadata.getTime() + ", id " + timedMetadata.getId() + ", metadata " +
timedMetadata.getMetadata() + ".");
/*if (!_timedMetadataList.contains(timedMetadata)) {
_timedMetadataList.add(timedMetadata);
}*/
/* scte35 */
if (timedMetadata.getName().equalsIgnoreCase("#EXT-OATCLS-SCTE35")) { PMPDemoApp.logger.i(LOG_TAG +
" inside ontimedmetadata"," ext"); parseSCTE35Tag(timedMetadata);
}
}
}
```

**その他の変更**

バージョン2.5では、次の追加変更も利用できます。

* `notifyClick()`メソッドは`MediaPlayerView`から`MediaPlayer`に移動しました。

* `AdPolicySelector` はインターフェイスで、クラスではありません。すべてのメソッドを実装します。
* `AdPolicyInfo` には、ではなく、のリストが含ま `AdBreakTimelineItem`れるようになり `AdBreakPlacement`ました。

* `ContentResolver`抽象クラスのAPI名が変更されました。
* `PlacementOpportunityDetector` は使用できなくなります。代わりに、`OpportunityGenerator`抽象クラスを拡張します。 次の例は、リファレンスの実装によって示されます。

* `AdBreakPlacement`コンストラクタのパラメータは同じですが、異なる順序で指定します。 実装例については、この製品にバンドルされているリファレンスプレイヤーの実装を参照してください。

## DRMの変更{#changes-in-drm}

このバージョンに加えられた変更の大部分はDRMレイヤーに含まれています。 次の表に、バージョン1.4と2.5の間のその他の変更点を示します。

| DRMManagerのメソッド | 1.4での成功コールバック | 1.4でのエラーコールバック | 2.5のリスナー |
|--- |--- |--- |--- |
| acquireLicense | DRMLicenseAccativedCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| acquirePreviewLicense | DRMLicenseAccativedCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| 認証する | DRMAuthenticationCompleteCallback | DRMOperationErrorCallback | DRMAuthenticateListener |
| createMetadataFromBytes | ナトリウム | DRMOperationErrorCallback | DRMErrorListener |
| initialize | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| joinLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| leaveLicenseDomain | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| resetDRM | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| returnLicense | DRMLicenseReturnCompleteCallback | DRMOperationErrorCallback | DRMReturnLicenseListener |
| setAuthenticationToken | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |
| storeLicenseBytes | DRMOperationCompleteCallback | DRMOperationErrorCallback | DRMOperationCompleteListener |

```java
//TVSDK 1.4
private final MediaPlayer.DRMEventListener _drmEventListener = new MediaPlayer.DRMEventListener() {

@Override
public void onDRMMetadata(final DRMMetadataInfo drmMetadataInfo) { PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata available
// event and the play event, so launch the metadata interface
// and give it the loaded metadata bytes, but only once
_drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo == null ||
!DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG + "#onDRMMetadata", "DRM auth is not needed."); return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold
// between the current player time and the DRM metadata start
// time. For the time being, we resolve it as soon as we receive
// the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG + "#onDRMMetadata", "DRMManager is null."); return;
}
SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity()); String authUser =
sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG + "#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(long majorCode,
long minorCode, Exception e) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + majorCode + " 0x" + Long.toHexString(minorCode));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};

//TVSDK 2.5
private final DRMMetadataInfoEventListener drmMetadataInfoEventListener = new DRMMetadataInfoEventListener() {
@Override
public void onDRMMetadataInfo(DRMMetadataInfoEvent drmMetadataInfoEvent) { final DRMMetadataInfo drmMetadataInfo =
drmMetadataInfoEvent.getDRMMetadataInfo();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.DRMEventListener#onDRMMetadata",
"DRM metadata available: " + drmMetadataInfo + ".");
if (getSuppressAutoPlayPreference() && drmMetadataInfo != null) {
// if suppress play setting, then the user is a tester who
// wishes to manually intervene between the metadata
// available event and the play event, so launch the
// metadata interface and give it the loaded metadata
// bytes, but only once
drmMetadata = drmMetadataInfo.getDRMMetadata();
}
if (drmMetadataInfo ==
null || !DRMHelper.isAuthNeeded(drmMetadataInfo.getDRMMetadata())) { PMPDemoApp.logger.i(LOG_TAG +
"#onDRMMetadata",
"DRM auth is not needed.");
return;
}
// Perform DRM auth.
// Possible logic might take into consideration a threshold between
// the current player time and the DRM metadata start time. For the
// time being, we resolve it as soon as we receive the DRM metadata.

DRMManager drmManager = _mediaPlayer.getDRMManager(); if (drmManager == null) {
PMPDemoApp.logger.e(LOG_TAG +
"#onDRMMetadata", "DRMManager is null.");
return;
}

SharedPreferences sharedPreferences = PreferenceManager.getDefaultSharedPreferences(getActivity());
String authUser = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_USERNAME,
getResources().getString(R.string.drmUsername));
String authPass = sharedPreferences.getString(PMPDemoApp.SETTINGS_DRM_PASSWORD,
getResources().getString(R.string.drmPassword));
DRMHelper.performDrmAuthentication(drmManager,
drmMetadataInfo.getDRMMetadata(), authUser,
authPass,
new DRMAuthenticationListener() {
@Override
public void onAuthenticationStart() { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationStart",
"DRM authentication started for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
@Override
public void onAuthenticationError(int major,
int minor,
String erroString, String serverErrorURL) {
if (getActivity() == null) { return;
}
PMPDemoApp.logger.e(LOG_TAG +
"#onAuthenticationError",
"DRM authentication failed. " + major +
" 0x" +
Long.toHexString(minor));
_handler.post(new Runnable() {
@Override
public void run() { showToast(getString(R.string.drmAuthenticationError)); getActivity().finish();
}
});
}
@Override
public void onAuthenticationComplete(byte[] authenticationToken) { PMPDemoApp.logger.i(LOG_TAG +
"#onAuthenticationComplete",
"Auth successful for DRM metadata at [" + drmMetadataInfo.getPrefetchTimestamp() + "].");
}
});
}
};
```

mediaplayerの作成後、1.4で使用可能だった静的`DRMManager`インスタンスは、`onDRMMetadataInfo`イベントリスナーのトリガー後に使用できるようになりました。

## 可変ビットレート(ABR)関連の変更{#adaptive-bitrate-abr-related-changes}

**定数の変更**

多くの定数は、型を`String`から`int`に変更しました。 次に例を示します。`MediaResourceType`、`ABRControlParameters`、`MediaPlayerStatusChangeEvent`。

```java
//TVSDK v1.4
ABRControlParameters
private void setAbrControlParams() { SharedPreferences sharedPreferences =
PreferenceManager.getDefaultSharedPreferences(getActivity());
if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED,
PMPDemoApp.DEFAULT_ABR_ENABLED)) {
int initialBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE, 0);
int minBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE, 0);
int maxBitRate = getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE, PMPDemoApp.DEFAULT_MAX_BIT_RATE);
int mbrPolicyAsInt =
getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, 0); ABRControlParameters.ABRPolicy abrPolicy = policyFromInt(mbrPolicyAsInt); abrPolicy = abrPolicy != null ?
abrPolicy : ABRControlParameters.ABRPolicy.ABR_MODERATE;
_mediaPlayer.setABRControlParameters(new ABRControlParameters(initialBitRate,
minBitRate, maxBitRate, abrPolicy));
}
}

//TVSDK v2.5
ABRControlParameters
private void setAbrControlParams() { ABRControlParametersBuilder abrBuilder =
new ABRControlParametersBuilder();

if (sharedPreferences.getBoolean(PMPDemoApp.SETTINGS_ABR_CTRL_ENABLED, PMPDemoApp.DEFAULT_ABR_ENABLED)) {

abrBuilder.setInitialBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_INITIAL_BITRATE,
ABRControlParameters.DEFAULT_ABR_INITIAL_BITRATE)); abrBuilder.setMinBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxPlayoutRate(getDoublePreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_PLAYOUT_RATE,
ABRControlParameters.DEFAULT_MAX_PLAYOUT_RATE)); abrBuilder.setMinTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MIN_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MIN_BITRATE)); abrBuilder.setMaxTrickPlayBitRate(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BITRATE,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE)); abrBuilder.setMaxTrickPlayBandwidthUsage(getIntPreference(sharedPreferences,
PMPDemoApp.SETTINGS_ABR_MAX_TRICKPLAY_BANDWIDTH,
ABRControlParameters.DEFAULT_ABR_MAX_BITRATE));

switch (getIntPreference(sharedPreferences, PMPDemoApp.SETTINGS_ABR_POLICY, -1)) {
case 0: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_CONSERVATIVE); break;
case 1: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_MODERATE); break;
case 2: abrBuilder.setPolicy(ABRControlParameters.ABRPolicy.ABR_AGGRESSIVE); break;
default: abrBuilder.setPolicy(ABRControlParameters.DEFAULT_ABR_POLICY);
}
}
_mediaPlayer.setABRControlParameters(abrBuilder.toABRControlParameters());
}
```

**ABRControlParametersコンストラクターの変更**

一部のパラメーターが追加され、名前が変更され、一部が移動されました。 v1.4ではコンストラクタのシグネチャ、2.5では新しいシグネチャを次に示します。

```java
//TVSDK v1.4
public ABRControlParameters(ABRPolicy abrPolicy,
int nInitialBitRate, int nMinBitRate,
int nMaxBitRate)

//TVSDK v2.5
public ABRControlParameters(int nInitialBitRate,
int nMinBitRate, int nMaxBitRate,
ABRPolicy abrPolicy,
int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate,
int nMaxTrickPlayBandwidthUsage, double dMaxPlayoutRate)
```

## エラーイベントと{#error-events-and-handling}の処理

**エラー処理の変更**

`MediaError`クラスは`Notification`クラスに置き換えられました。 クラス`MediaError`と`Notification`の唯一の違いは、後者のクラスにdescription属性が含まれていないことです。 TVSDK 2.5には、値101xxx、102xxx、104xxx、106xxx、107xxx、109xxxのTVSDK 1.4エラーコードは存在しません。TVSDK 2.5の再生コードについては、[ネイティブのエラー — ビデオ再生値&lt;a1を参照してください。/>。](assets/psdk_android_2.5.pdf)

TVSDK 1.4および2.5でのエラー処理の例を次に示します。

```java
//TVSDK v1.4
@Override
public void onStateChanged(MediaPlayer.PlayerState state, MediaPlayerNotification notification) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");

switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR: PMPDemoApp.logger.e(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: " + notification + "."); getActivity().finish();
break;
default:
// do nothing
}
}

//TVSDK v2.5
private final StatusChangeEventListener statusChangeEventListener = new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent mediaPlayerStatusChangeEvent)
{
MediaPlayerStatus state = mediaPlayerStatusChangeEvent.getStatus(); PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Player state changed to [" + state
+ "].");
switch (state) {
// Non recoverable state - either reset player and reinitialize
// or release the player and create a new one.
case ERROR:
PMPDemoApp.logger.e(LOG_TAG + "::MediaPlayer.PlayerStateEventListener#onStateChanged()", "Error: ");
printErrorMetadata(mediaPlayerStatusChangeEvent.getMetadata()); showToast("MediaPlayer status ERROR: Look at the logs for details"); getActivity().finish();
break;
default:
// do nothing
}
}
};
```

回復可能なすべてのエラーは警告として扱われ、TVSDK 2.5の`NotificationEventListener`を使用して処理されます。警告は、TVSDK 1.4のQOSハンドラーに`onOperationFailed`リスナーと共に通知として表示されます。TVSDK 2.5とは別のイベントです。 1.4および2.5で処理される警告は、次のとおりです。

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener()
{
@Override
public void onBufferStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
}
@Override
public void onBufferComplete() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
}
@Override
public void onSeekStart() {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
}
@Override
public void onSeekComplete(long adjustedTime) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
}
@Override
public void onLoadInfo(LoadInfo loadInfo) {
PMPDemoApp.logger.i(LOG_TAG + "::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize() + " bytes, media duration: " + loadInfo.getMediaDuration() + "ms, download duration: " + loadInfo.getDownloadDuration() + "ms");
}
@Override
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - ").append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append

//TVSDK v2.5
private final NotificationEventListener notificationEventListener = new NotificationEventListener() {
/**
* An example of dumping the information within a Notification. Here, we don't handle the event in
* any way except to print a log message.
* @param event The NotificationEvent
*/
@Override
public void onNotification(NotificationEvent event) { Notification notification = event.getNotification(); Notification.Type type = notification.getType(); StringBuilder sb = new StringBuilder(); sb.append("[").append(type).append("]");
sb.append(" Player operation failed (").append(notification.getCode()).append(")"); Metadata metadata = notification.getMetadata();
if (metadata != null)
{
for (String key : metadata.keySet())
{
sb.append(", ").append(key).append(" = ").append(metadata.getValue(key));
}
}
Notification inner = notification.getInnerNotification(); if (inner != null) {
sb.append(" :: Inner Notification [").append(inner.getType()).append("](").append(inner.getCode()).append(")");
Metadata innerMetadata = inner.getMetadata(); if (innerMetadata != null) {
for (String iKey : innerMetadata.keySet()) { sb.append(", ").append(iKey).append(" =
").append(innerMetadata.getValue(iKey));
}
}
}
switch(type)
{
case ERROR:
PMPDemoApp.logger.e(LOG_TAG, sb.toString()); break;
case WARNING:
PMPDemoApp.logger.w(LOG_TAG, sb.toString()); break;
default:
PMPDemoApp.logger.i(LOG_TAG, sb.toString()); break;
}
showToast(sb.toString()); PMPDemoApp.logger.d(LOG_TAG, sb.toString());
}
};
```

**新しい例外**

TVSDK v1.4ではNULL、エラーの戻り値、様々な例外(`MediaPlayerException`、`IllegalStateException`、`IllegalArgumentException`)の組み合わせを使用していましたが、TVSDK v2.5 `generatesMediaPlayerException`ではすべてのエラーが報告されます。

>[!NOTE]
>
>MediaPlayerExceptionの詳細を取得するには、`getErrorCode()`を使用できます。

変更の例を次に示します。

```java
//TVSDK v1.4
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (IllegalArgumentException e) { PrimetimeReference.logger.w(LOG_TAG +
"#setBufferControlParams",
"Unable to apply buffering params: " + e.getMessage() + ".");
}
}

//TVSDK v2.5
public void setBufferControlParams() { try {
mediaPlayer.setBufferControlParameters(getBufferParamsFromSettings());
} catch (MediaPlayerException e) { PrimetimeReference.logger.w(LOG_TAG + "#setBufferControlParams", "Unable to apply buffering params: " + e.getMessage() + ".");
}
}
```

## QOSパラメーター{#changes-to-qos-parameters}の変更

QOSProviderオブジェクトプロパティには若干の変更があります。

* `TimeToFirstFrame`はTVSDK 2.5では使用できません。
* TVSDK 2.5 QOSProviderには、ストリーミングセッション中に認識される帯域幅を決定する新しいプロパティがあります。

```java
//TVSDK v1.4
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitrate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart()); setQosItem("Time to first frame", (int) playbackInformation.getTimeToFirstFrame()); setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare()); setQosItem("Last seek time", (int) playbackInformation.getLastSeekTime());
}

//TVSDK v2.5
public void updateQosInformation(PlaybackInformation playbackInformation) { if (playbackInformation == null) {
return;
}
setQosItem("Frame rate", (int) playbackInformation.getFrameRate() +
" (" + (int) playbackInformation.getDroppedFrameCount() + " dropped)"); setQosItem("Bitrate", (int) playbackInformation.getBitRate()); setQosItem("Buffering time", (long) playbackInformation.getBufferingTime()); setQosItem("Buffer length", (long) playbackInformation.getBufferLength()); setQosItem("Buffer time", (long) playbackInformation.getBufferTime()); setQosItem("Empty buffer count", (int) playbackInformation.getEmptyBufferCount()); setQosItem("Time to load", (int) playbackInformation.getTimeToLoad()); setQosItem("Time to start", (int) playbackInformation.getTimeToStart());
setQosItem("Time to prepare", (int) playbackInformation.getTimeToPrepare());
setQosItem("Perceived Bandwidth", (int) playbackInformation.getPerceivedBandwidth());
```

* `QOSEventListener::onOperationFailed()`は、TVSDK 2.5には存在しません。このイベントリスナーに表示される警告は、現在は`NotificationEventListener::onNotification()`イベントリスナーに表示されます。

* `QOSProvider event listeners onBufferStart()`、`onBufferComplete()`、`onSeekStart()`、`onSeekComplete()`および`onLoadInfo()`は、mediaPlayerインスタンスを使用してバインドされる個々のイベントリスナーです。

```java
//TVSDK v1.4
private final MediaPlayer.QOSEventListener _qosEventListener = new MediaPlayer.QOSEventListener() {

@Override
public void onBufferStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
@Override
public void onBufferComplete() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()", "Buffering complete.");
hideBufferingSpinner();
}
@Override
public void onSeekStart() { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
@Override
public void onSeekComplete(long adjustedTime) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " +
adjustedTime + ".");
_controlBar.setPosition(adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayer.PlayerState.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayer.PlayerState.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
@Override
public void onLoadInfo(LoadInfo loadInfo) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onLoadInfo()", "Url: " +
loadInfo.getUrl() + ", size: " + loadInfo.getSize() +
" bytes, media duration: " +
loadInfo.getMediaDuration() + "ms, download duration: " +
loadInfo.getDownloadDuration() + "ms");
 
public void onOperationFailed(MediaPlayerNotification.Warning warning) {

StringBuffer sb = new StringBuffer("Player operation failed: "); sb.append(warning.getCode()).append(" - ").append(warning.getDescription()); if (warning.getMetadata() != null) {
sb.append("Warning metadata: ").append(warning.getMetadata().toString());
}

MediaPlayerNotification innerNotification = warning.getInnerNotification(); registerFailedAudioTrackIndex(innerNotification); handleFailedSeekEvent(innerNotification);

while (innerNotification != null) { sb.append("Inner notification: ");
sb.append(innerNotification.getCode()).append(" - "). append(innerNotification.getDescription());
Metadata metadata = innerNotification.getMetadata(); if (metadata != null) {
for (String key : metadata.keySet()) { sb.append(" - ").append(key).append(": ").
append(metadata.getValue(key));
}
}
innerNotification = innerNotification.getInnerNotification();
}
String errMsg = sb.toString(); PMPDemoApp.logger.w(LOG_TAG +
"::MediaPlayer.QOSEventListener#onOperationFailed()", errMsg);
showToast(errMsg);
}
};

//TVSDK v2.5
mediaPlayer.addEventListener(MediaPlayerEvent.LOAD_INFORMATION_AVAILABLE,
loadInfoEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_BEGIN,
bufferingBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.BUFFERING_END,
bufferingEndEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_BEGIN,
seekBeginEventListener); mediaPlayer.addEventListener(MediaPlayerEvent.SEEK_END,
seekEndEventListener);
// Buffering events.
BufferingBeginEventListener bufferingBeginEventListener = new BufferingBeginEventListener() {
@Override
public void onBufferingBegin(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferStart()", "Buffering started.");
showBufferingSpinner();
}
};

BufferingEndEventListener bufferingEndEventListener = new BufferingEndEventListener() {
@Override
public void onBufferingEnd(BufferEvent bufferEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onBufferComplete()",
"Buffering complete."); hideBufferingSpinner();
}
};

BufferPreparedEventListener bufferPreparedEventListener = new BufferPreparedEventListener() {
@Override
public void onBufferPrepared() {
}
};
// seek events.
SeekBeginEventListener seekBeginEventListener = new SeekBeginEventListener() {

@Override
public void onSeekBegin(SeekEvent seekEvent) { PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekStart()", "Seek starting.");
inTrickPlayMode = false;
}
};
SeekEndEventListener seekEndEventListener = new SeekEndEventListener() {
@Override
public void onSeekEnd(SeekEvent seekEvent) {
double adjustedTime = seekEvent.getActualPosition();
PMPDemoApp.logger.i(LOG_TAG +
"::MediaPlayer.QOSEventListener#onSeekComplete()", "Seek complete at position: " + adjustedTime + ".");
_controlBar.setPosition((long) adjustedTime);
if (adjustedTime == _mediaPlayer.getPlaybackRange().getEnd() &&
_mediaPlayer.getStatus() == MediaPlayerStatus.COMPLETE) {
// Show the replay button. showReplayButton();
}
if (_mediaPlayer.getStatus() == MediaPlayerStatus.PAUSED) {
// Show the pause icon.
_controlBar.pause();
}
}
};
/**
* LoadInformationEventListener that intercepts PSDK load info events
*/
private final LoadInformationEventListener loadInfoEventListener = new LoadInformationEventListener() {

@Override
public void onLoadInformation(LoadInformationEvent event) { LoadInformation loadInfo = event.getLoadInfomation(); PMPDemoApp.logger.i(
LOG_TAG + "::LoadInformationEventListener#onLoadInfomation()", "Url: " + loadInfo.getUrl() + ", size: "
+ loadInfo.getSize()
+ " bytes, download duration: "
+ loadInfo.getDownloadDuration() + "ms");
}
};
```

## 役立つリソース{#helpful-resources}

* [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html)のページにある完全なヘルプドキュメントを参照してください。