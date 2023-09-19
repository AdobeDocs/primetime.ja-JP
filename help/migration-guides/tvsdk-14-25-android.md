---
title: Android 向け TVSDK 1.4～2.5(Java)
description: TVSDK 2.5 は、パフォーマンス、セキュリティ、優れた統合などの点で、バージョン 1.4 に対して複数のメリットを提供します。
contentOwner: vishgupt
products: SG_PRIMETIME
topic-tags: migration
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 0%

---

# Android 向け TVSDK 1.4～2.5(Java) {#tvsdk-to-for-android-java}

TVSDK 2.5 は、パフォーマンス、セキュリティ、優れた統合などの点で、バージョン 1.4 に対して複数のメリットを提供します。

TVSDK は、最も重要なデバイス上で、最も大きな課題を解決します。 Android は世界的な優位性を維持し、市場シェアの 86%以上を占めています。 Android での TVSDK への移行により、再生パフォーマンスが最適化され、ユーザーエンゲージメントが向上し、新しいコンテンツ形式のサポートにより市場投入までの時間が短縮されます。

## TVSDK v2.5 への移行のメリット {#benefits-of-migrating-to-tvsdk-v}

TVSDK 2.5 は、パフォーマンス、セキュリティ、優れた統合などの点で、バージョン 1.4 に対して複数のメリットを提供します。 この新しいバージョンへの移行のメリットをすばやく知るには、以下に説明します。

サードパーティのベンチマーク調査によると、v2.5 では、起動時間が 5 倍に短縮され、業界平均でドロップフレームが 3.8 倍に短縮されます。

| パフォーマンスの機能 | 説明 |
|--- |--- |
| VOD および Live の即時オン | チャネルの切り替え時に、TV（エクスペリエンスなど）の即時再生用の初期 ts セグメントを、VOD およびライブリニアストリームでプリロードします。 |
| 遅延広告読み込み | 並列スレッドでミッドロール広告を解決中に、プリロールまたはコンテンツが使用可能になるとすぐに再生を開始します。 |
| 永続的なネットワーク接続 | 再生パフォーマンスを高めるため、ネットワークコードの効率の向上と待ち時間の短縮。 |
| ABR ロジックの改善 | 新しい ABR ロジックは、バッファ長、バッファ長の変化率、測定された帯域幅に基づいています。 これにより、ABR は帯域幅が変動する際に適切なビットレートを選択し、また、バッファ長の変化率を監視することで、ビットレート切り替えが実際に発生する回数を最適化します。 |
| 部分的なセグメントのダウンロード | クライアント側でビデオを確実にレンダリングするために、セグメントから十分なフレームが利用可能になるとすぐに再生を開始します。 |
| 並列ダウンロード | TVSDK は、オーディオおよびビデオセグメントを並行してダウンロードし、非圧縮コンテンツで再生パフォーマンスを最適化します。 |

再生機能を使用すると、デジタル上で線形放送のエクスペリエンスを配信することで、消費者のエンゲージメントを向上できます。 また、Widevine などのネイティブ DRM を HD 再生に活用するのに役立ちます。

| 再生機能 | 説明 |
|--- |--- |
| MP4 再生 | MP4 の短いクリップは、TVSDK 内での再生に再変換する必要はありません。 |
| DASH VOD コンテンツ再生 | 基本的な DASH VOD 再生の使用例がサポートされています。 |
| ABR を使用したスムーズなトリック再生 | 低速のキーフレームと高速の I-Frame を使用した HLS での早送りと巻き戻しのサポート。 サポートされるすべてのフレームに対する ABR のサポート。 |

ネイティブ DRM での HD 再生など、スタジオの制限を満たすには、この機能が重要です。

| 機能 | 説明 |
|--- |--- |
| 解像度に基づく出力保護 | 再生は、DRM 要件で許可される特定の解像度にのみ制限できます。 Primetime DRM でのみ使用できます。 |
| Widevine のサポート | ネイティブ DRM の使用例を有効にする DASH VOD ストリームでサポートされます。 |

直接請求の機能強化により、毎月請求用に手動レポートを作成する必要がなくなりました。 VHL 2.0 を使用すると、ビルド前の統合により、市場投入までの時間を短縮でき、トラッキングの精度を向上できます。

| 機能 | 説明 |
|--- |--- |
| Mort 統合 | Mort からの広告視認性測定のサポート。 |
| VHL 2.0 | Adobe Analyticsの使用状況データを自動収集するための、最新の最適化されたビデオハートビートライブラリ統合。 |
| フェイルオーバーのサポート | ホストサーバー、プレイリストファイル、セグメントに障害が発生した場合でも、再生を中断せずに続行するための追加戦略が実装されました。 |
| 直接請求の統合 | Adobe Primetimeが顧客が使用するストリームに関して認定したAdobe Analyticsバックエンドに請求指標を送信します。 |

>[!NOTE]
>
>マルチ CDN のサポートを除き、 TVSDK v1.4 のすべての機能が v2.5 でサポートされます。

## 移行プロセスの概要 {#overview-of-the-migration-process}

TVSDK 1.4 から 2.5 へのスムーズな移行に伴い、バージョン 2.5 ライブラリに変更し、再コンパイルしてから、このドキュメントを使用して、発生した問題をデバッグできます。

TVSDK v1.4 ライブラリは v2.5 ライブラリとは連携せず、共存しません。 TVSDK 2.5 で v2.5 ライブラリを使用し、TVSDK 2.5 にアップグレードするには、アプリケーションと統合を移行する必要があります。このドキュメントでは、アプリケーションコードの変更方法と変更内容、および再コンパイル中のエラーに対処する方法について説明します。

psdk.jar ファイルは、様々な機能をサポートするためにサードパーティのライブラリを使用します。 ライブラリが削除されないようにするには、以下を `proguard.cfg` ファイル：

```java
# Adobe TVSDK keep classes
-keep class com.adobe.** { *; }
-keep class com.google.android.exoplayer.**
{ *; }
```

Adobe Analytics の `build.gradle` ファイルの場合、TVSDK ベースの JAR ファイルを含めるために compile ディレクティブを含める必要があります。 アプリにAdobeビデオ分析が含まれる場合、Adobeビデオ分析の統合に必要な追加の jar に対して compile ディレクティブをアプリに含める必要があります

```java
# Compile Adobe TVSDK jars compile files('libs/psdk-va.jar')
compile files('libs/VideoHeartbeat.jar')
```

このドキュメントでは、複数のマイナーな変更については説明しません。 API の小さな変更点については、 [Android Java API 用 TVSDK 2.5](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/index.html). 対応する C++ API リファレンスには、詳細な説明が記載されています。 類似の C++ API ドキュメントについては、 [Android C++ API 用 TVSDK 2.5](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.5/index.html).

API の使用例は、 TVSDK で配布されているリファレンス実装で複数説明されています。

## TVSDK v2.5 における API の変更 {#api-changes-in-tvsdk-v}

新しい API、古い API、変更された API については、以下で説明します。

| TVSDK v1.4 | TVSDK v2.5 | 説明 |
|--- |--- |--- |
| com.adobe.ave.drm .DRMAcquireLicenseSettings を読み込む | import com.adobe.mediacore.drm .DRMAcquireLicenseSettings; | TVSDK 2.5 API のすべてのクラス名は、 com.adobe.mediacore というプレフィックスで始まります。 これは一例に過ぎません。 |
| MediaPlayerException、IllegalStateException、または IllegalArgumentException | MediaPlayerException | 2.5 では、API は MediaPlayerException のみを生成します。 |
| MediaPlayer.PlayerState (MediaPlayer.Event.PLAYBACK) | MediaPlayerStatus (MediaPlayerEvent.STATUS_CHANGED) | v2.5 では、 MediaPlayer.PlayerState の名前が別の列挙 MediaPlayerStatus に変更されました。 |
| DefaultMediaPlayer.create (getActivity().getApplicationContext()) | MediaPlayer mediaPlayer = new MediaPlayer(getActivity(). getApplicationContext()); | オブジェクトの作成に使用される静的メソッドは、パブリックコンストラクタに置き換えられます。 |
| MediaPlayer.seekToLocalTime() | MediaPlayer.seekToLocal() | MediaPlayer.seekToLocalTime() メソッドは、現在は MediaPlayer.seekToLocal() と呼ばれています。 |
| closedCaptionsTrack.isActive() |  | 利用不可 |
| MetadataNode | メタデータ | v2.5 では、Metadata クラスが v1.4 MetadataNode クラスの使用を置き換えます。 |
| DefaultMetadataKeys | MetadataKeys | v1.4 の DefaultMetadataKeys は v2.5 列挙 MetadataKeys にあります。 |
| AdvertisingFactory | ContentFactory | v1.4 からの AdvertisingFactory の名前が v2.5 で ContentFactory に変更されました。 |
| PlacementOpportunityDetector | OpportunityGenerator | ディテクターはジェネレーターに置き換えられます。 |
| mediaPlayer.getView().notifyClick(); | mediaPlayer.notifyClick(); | MediaPlayerView の notifyClick() メソッドは、 MediaPlayer クラスに移動されました。 |
| public ABRControlParameters(ABRPolicy abrPolicy, int nInitialBitRate, int nMinBitRate, int nMaxBitRate) | public ABRControlParameters(int nInitialBitRate, int nMinBitRate, int nMaxBitRate, ABRPolicyPolicy, int nMinTrickPlayBitRate, int nMaxTrickPlayBitRate, intNNmaxTrickPlayBandwidthUsage, double dMaxPlayoutRate) |  |
| playbackInformation.getTimeToFirstFrame() |  | 利用不可 |
|  | playbackInformation.get IntercedBandwidth() | TVSDK v2.5 QOSProvider には、ストリーミングセッション中に認識される帯域幅を決定する新しいプロパティがあります。 |

### 削除されたクラス {#removed-classes}

次のクラスは削除され、同等のクラスはありません。

* `TimeRangeCollection`
* `PSDKConfig`
* `BaseLogger`
* `DefaultLogger`
* `Log`
* `Logger`
* `LogFactory`
* `NullLogger`

これらのクラスの最後の 6 つは、参照実装でユーティリティクラスとして使用できます。

## 名前空間の変更 {#namespace-changes}

TVSDK 2.5 API は名前空間を統合します。

TVSDK 2.5 API のすべてのクラス名は、 com.adobe.mediacore というプレフィックスで始まります。 TVSDK 1.4 API の一部のクラス名は com.adobe.ave で始まります。 対応する 2.5 クラスは、com.adobe.ave を com.adobe.mediacore に変更します。 例えば、1.4 および 2.5 のコードの次の行の変更点に注意してください。

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

## イベント処理の変更点 {#changes-in-event-handling}

このバージョンにイベントを登録するには、ハンドラーをに渡します。 `addEventListener`. イベントのリストがバージョン 1.4 からバージョン 2.5 に大幅に変更されました。\
例えば、次に、 `MediaPlayerEvent.STATUS_CHANGED:`

```java
mPlayer.addEventListener(MediaPlayerEvent.STATUS_CHANGED,
new StatusChangeEventListener() {
@Override
public void onStatusChanged(MediaPlayerStatusChangeEvent event) {
//Handle status change event
}
});
```

1.4 でのイベントの登録方法は次のとおりです。

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

MediaPlayerEvent 列挙には、すべてのイベントコードが含まれます。 1.4 の次のイベントコードは、2.5 には存在しなくなりました。

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

2.5 では、次のイベントコードが新しく追加されました。

* `AD_RESOLUTION_COMPLETE`
* `BUFFER_PREPARED`
* `CAPTIONS_UPDATED`
* `MANIFEST_UPDATED`
* `PLAYBACK_RANGE_UPDATED`
* `RESERVATION_REACHED`
* `TIME_CHANGED`
* `TIMED_EVENT`
* `TIMED_METADATA_ADDED_IN_BACKGROUND`

### 名前が変更されたイベント {#renamed-events}

| 新しい名前 | 以前の名前 |
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

## MediaPlayer の変更 {#mediaplayer-changes}

新しい構築方法 `MediaPlayer` メソッドの一部に対する変更。

**MediaPlayer クラスの変更**

以下に変更点を示します。 `MediaPlayer` クラス：

* The `MediaPlayerStatus` 列挙置換 `MediaPlayer.PlayerState`. 例：

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

* The `MediaPlayer.seekToLocalTime()` メソッドが `MediaPlayer.seekToLocal`. 例：

```java
//TVSDK v1.4
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocalTime(localPosition);
}

//TVSDK v2.5
public void seekToLocal(long localPosition) { mediaPlayer.seekToLocal(localPosition);
}
```

* The `MediaPlayerView.notifyClick()` メソッドは現在 `MediaPlayer.notifyClick()`. 例：

```java
//TVSDK v1.4
public void adClick() { mediaPlayer.getView().notifyClick();
}

//TVSDK v2.5
public void adClick() { mediaPlayer.notifyClick();
}
```

* 前者は `MediaPlayer.MediaPlayer.getNotificationHistory()` メソッドは現在削除され、置き換えられませんでした。
* 前者は `MediaPlayer.replaceCurrentItem()` は次の 2 つの方法に分割されます。 `replaceCurrentResource()`：のインスタンスを取得します。 `MediaResource`、および `replaceCurrentItem()`：のインスタンスを取得します。 `MediaPlayerItem`. 例：

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

これを使用して、ブラックアウトの場合と同様に、初期化済みの MediaPlayer インスタンスを切り替えることができます。

**コンストラクタは、静的 create() メソッドを置き換えます。**

TVSDK v2.5 では、 `create()` TVSDK v1.4 のメソッド。名前がデフォルトで始まるすべてのクラス。例： `DefaultMediaPlayer`, `DefaultNetworkConfig`, `DefaultContentFactory`、v2.5 では使用できません。

場合によっては、 TVSDK v1.4 API は次のパターンを使用してクラスを作成します。

1. インターフェイスを定義します ( 例： `MediaPlayer`) をクリックします。
1. デフォルトのクラスを指定します ( 例： `DefaultMediaPlayer`) をクリックします。
1. 次を提供： `create()` メソッドをデフォルトクラスに設定し、インターフェイスを実装するクラスを指定します。

TVSDK v2.5 では、このようなインターフェイスは具体的なクラスであり、それぞれのコンストラクターを使用してこれらのクラスのインスタンスを作成します。 次のコードスニペットに、この違いを示します。

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

このパターンに従わず、を使用する他のクラス `create()` 1.4 のメソッドには、以下が含まれます。

* MediaResource\
  これは以前使用した `MediaResource.createFromUrl()`. 次に、URL、リソースタイプおよびメタデータを取るコンストラクターを使用します。 例：

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

一部のクラス ( 例： `ContentFactory`) は、公開されているデフォルト実装がない抽象クラスです ( 例： `DefaultContentFactory`) をクリックします。 この場合、次のような便利な関数を使用してデフォルトの実装を指定できます。 `mediaPlayerItemConfig.getDefaultContentFactory()`

**クローズドキャプションの変更**

次の変更は、クローズドキャプションに関連するクラスに影響します。

* クローズドキャプショントラックを取得する場合、 `MediaPlayerItem.getClosedCaptionTracks()` は、アクティブなトラックのみを返します。
* `ClosedCaptionTrack` 現在は、 `isActive()` メソッド。

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

## 広告の変更 {#advertising-changes}

バージョン 2.5 には、広告関連の変更がいくつかあります。

**広告行動の変更**

ユーザーが広告ポッドを超えてシークを実行した場合の広告再生のデフォルトの動作は、v2.5 では少し変化します。広告ブレークが視聴されない場合、広告は、シークフォワード後に再生されます。 アプリがデフォルトの広告ポリシーを使用している場合、広告の時間は、再生が完了した後に削除されます。 TVSDK v2.5 を使用して、ユーザーがタイムライン上の広告ポッドの背後にシークし、広告の時間が視聴されていない場合、広告は再生されません。

ただし、 TVSDK v1.4 では、デフォルトでは、シークバックバック時に広告が再生されます。 例えば、3 番目と 4 番目の広告の時間の間を逆方向にシークした場合、 TVSDK v1.4 のデフォルトの動作では、3 番目の広告の時間を再生します。

**広告ルールの変更**

広告ルールは JSON ファイルを使用して指定されます。 JSON ファイルの形式は、両方のバージョンの TVSDK で同じになります。 ただし、TVSDK v2.5 では、広告ルールの JSON ファイルは、HTTP URL を介してアクセス可能な場所でホストする必要があります。 アプリケーションは、 AuditudeSettings のインスタンスを使用できます。

```java
//TVSDK v2.5
AuditudeSettings result = new AuditudeSettings(); result.setCRSRulesJsonURL(<http url of AdobeTVSDKConfig.json>);
```

TVSDK バージョン 1.4 では、このファイルはアプリケーションの assets フォルダーの下に配置され、TVSDK がこのファイルを読み込みます。

**広告ファクトリ名の変更**

`AdvertisingFactory` は現在、 `ContentFactory`. を使用 `ContentFactory` メソッドの一部を上書きして、カスタマイズされた広告ワークフローを作成できます。 デフォルトの動作を維持するには、次のように return null を使用します。

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

**長さ 0 の広告ブレーク**

TVSDK 2.5 は、広告サーバーが広告を返さない場合に、長さ 0 の広告ブレークをプレースホルダーとして挿入します。

長さが 0 の広告の時間は、onAdBreakStarted イベントを使用して広告の時間で 0 になる広告の数を検出することで決定でき、アプリケーションは、それに応じてこれらの広告の時間を処理する必要があります。

**メタデータの変更**

Metadata クラスは、以前の MetadataNode クラスに対して、より有効な置き換えを提供します。

* Metadata クラスには、文字列、バイト配列およびその他の Metadata オブジェクトを格納できます。

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

* The `MetadataKeys` 列挙置換 `DefaultMetadataKeys`. のすべてのキーではありません `DefaultMetadataKeys` が新しいバージョンに存在する。

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

* 広告メタデータが `AdvertisingMetadata` クラス、Metadata のサブクラス、現在は `MediaPlayerItemConfig` ではなく `MediaResource`.

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

ネットワーク設定メタデータ ( 以前は `MediaResource` クラスの `NetworkConfiguration` クラスに格納され、現在はに格納されています。 `MediaPlayerItemConfig` ではなく `MediaResource`.

```java
//TVSDK v1.4
MediaResource playerResource = MediaResource.createFromUrl(url, mediaMetadata);
...

//TVSDK v2.5
MediaPlayerItemConfig mediaItemConfig = new MediaPlayerItemConfig(context);

NetworkConfiguration mediaNetworkConfiguration = mediaItemConfig.getNetworkConfiguration();
```

**TimedMetadata 解析の変更**

の解析 `TimedMetadata` は、ID3 タグを解析するためのデータ型に関して 2.5 で変更されました。

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

バージョン 2.5 では、次のその他の変更が利用できます。

* The `notifyClick()` メソッドは次の場所から移動されました： `MediaPlayerView` から `MediaPlayer`.

* `AdPolicySelector` は、クラスではなくインターフェイスです。 すべてのメソッドを実装します。
* `AdPolicyInfo` に次のリストが含まれるようになりました： `AdBreakTimelineItem`，ではない `AdBreakPlacement`.

* の API 名 `ContentResolver` 抽象クラスが変更されます。
* `PlacementOpportunityDetector` は使用できなくなりました。 代わりに、 `OpportunityGenerator` 抽象クラス。 参照実装は、この例を示しています。

* のパラメーター `AdBreakPlacement` コンストラクタは同じですが、順序は異なります。 実装例については、製品にバンドルされているリファレンスプレーヤーの実装を参照してください。

## DRM の変更 {#changes-in-drm}

このバージョンでの変更の大部分は DRM レイヤーに含まれています。 次の表に、バージョン 1.4 と 2.5 の追加の変更を示します。

| DRMManager メソッド | 1.4 での成功コールバック | 1.4 でのエラーコールバック | 2.5 のリスナー |
|--- |--- |--- |--- |
| acquireLicense | DRMLicenseAccuriatedCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| acquirePreviewLicense | DRMLicenseAccuriatedCallback | DRMOperationErrorCallback | DRMAcquireLicenseListener |
| 認証 | DRMAuthenticationCompleteCallback | DRMOperationErrorCallback | DRMAuthenticateListener |
| createMetadataFromBytes | 該当なし | DRMOperationErrorCallback | DRMErrorListener |
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

静的 `DRMManager` mediaplayer の作成後に 1.4 で使用可能になったインスタンスは、 `onDRMMetadataInfo` イベントリスナーがトリガーされます。

## 可変ビットレート (ABR) 関連の変更 {#adaptive-bitrate-abr-related-changes}

**定数の変更**

多くの定数が次の型から変更されました： `String` から `int`. 例： `MediaResourceType`, `ABRControlParameters`、および `MediaPlayerStatusChangeEvent`.

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

**ABRControlParameters コンストラクターの変更**

一部のパラメータが追加され、一部のパラメータの名前が変更され、一部が移動されました。 v1.4 でのコンストラクタシグネチャと 2.5 での新しいシグネチャは次のとおりです。

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

## エラーイベントと処理 {#error-events-and-handling}

**エラー処理の変更**

The `MediaError` クラスは `Notification` クラス。 クラス間の唯一の違い `MediaError` および `Notification` は、後者に description 属性が含まれていないことを表します。 値が 101xxx、102xxx、104xxx、106xxx、107xxx、109xxx の TVSDK 1.4 のエラーコードは、TVSDK 2.5 には存在しません。TVSDK 2.5 の再生コードについては、 [ネイティブエラー — ビデオ再生値](assets/psdk_android_2.5.pdf).

TVSDK 1.4 および 2.5 でのエラー処理の例を以下に示します。

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

回復可能なエラーはすべて警告として扱われ、 `NotificationEventListener` （ TVSDK 2.5 用）警告は通知として表示され、 `onOperationFailed` TVSDK 1.4 の QOS ハンドラー内のリスナー。TVSDK 2.5 と同様に、通知は別のイベントです。 1.4 および 2.5 で処理される警告は次のとおりです。

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

TVSDK v1.4 では NULL、エラー戻り値、様々な例外 ( `MediaPlayerException`, `IllegalStateException`、および `IllegalArgumentException`), TVSDK v2.5 `generatesMediaPlayerException` （すべてのエラー）。

>[!NOTE]
>
>MediaPlayerException の詳細を取得するには、 `getErrorCode()`.

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

## QOS パラメーターの変更 {#changes-to-qos-parameters}

QOSProvider オブジェクトのプロパティには、次のような小さな変更があります。

* The `TimeToFirstFrame` は、 TVSDK 2.5 では使用できません。
* TVSDK 2.5 QOSProvider には、ストリーミングセッション中に認識される帯域幅を決定する新しいプロパティがあります。

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

* The `QOSEventListener::onOperationFailed()` は TVSDK 2.5 に存在しなくなりました。このイベントリスナーで以前に表示されていた警告が、 `NotificationEventListener::onNotification()` イベントリスナー。

* The `QOSProvider event listeners onBufferStart()`, `onBufferComplete()`, `onSeekStart()`, `onSeekComplete()`、および `onLoadInfo()` は、mediaPlayer インスタンスにバインドされる個々のイベントリスナーです。

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

## 役立つリソース {#helpful-resources}

* 完全なヘルプドキュメントは、 [Adobe Primetimeラーニングとサポート](https://helpx.adobe.com/support/primetime.html) ページに貼り付けます。
