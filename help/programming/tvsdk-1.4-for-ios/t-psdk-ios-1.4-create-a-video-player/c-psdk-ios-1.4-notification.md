---
description: プレイヤーは、プレイヤーの状態を示す一連のイベントをリッスンできます。
title: 通知の設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---


# 通知の設定{#set-up-notifications}

プレイヤーは、プレイヤーの状態を示す一連のイベントをリッスンできます。

`PTMediaPlayer`がクライアントプレーヤーのプロパティであると仮定し、次の例の`self.player`は`PTMediaPlayer`インスタンスを表します。 次の例は、PTMediaPlayerの設定手順に示され、ほとんどの通知を含む`addObservers`メソッドを実装します。

```
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerStatusChange:)  
      name:PTMediaPlayerStatusNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
      name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerTimeChange:)  
      name:PTMediaPlayerTimeChangeNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayStarted:)  
      name:PTMediaPlayerPlayStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemPlayCompleted:)  
      name:PTMediaPlayerPlayCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemTimelineChanged:)  
      name:PTMediaPlayerTimelineChangedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerItemMediaSelectionOptionsAvailable:)  
      name:PTMediaPlayerMediaSelectionOptionsAvailableNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
      name:PTMediaPlayerAdBreakStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
      name:PTMediaPlayerAdBreakCompletedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayStarted:)  
      name:PTMediaPlayerAdStartedNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayProgress:)  
      name:PTMediaPlayerAdProgressNotification object:self.player]; 
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdPlayCompleted:)  
      name:PTMediaPlayerAdCompletedNotification object:self.player]; 
```

## iOS通知{#section_65D9B2DBF5574313BD3218AB02242BBB}

`ThePTMediaPlayerNotifications` クラスは、TVSDKがプレイヤーにディスパッチする通知をリストします。

<table frame="all" colsep="1" rowsep="1" id="table_ios_notifications"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>通知</b> </td> 
   <td colname="2"> <b>意味</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakCompletedNotification  </span> </td> 
   <td colname="2"> 広告の時間が終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakStartedNotification  </span> </td> 
   <td colname="2"> 広告の時間が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdClickNotification  </span> </td> 
   <td colname="2"> ユーザーがバナー広告をクリックしました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdCompletedNotification  </span> </td> 
   <td colname="2"> 個々の広告が終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdProgressNotification  </span> </td> 
   <td colname="2"> 広告が進行した。広告の再生中、常にディスパッチされます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdStartedNotification  </span> </td> 
   <td colname="2"> 個々の広告が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTBackgroundManifestErrorNotification  </span> </td> 
   <td colname="2"> バックグラウンドマニフェストのダウンロードに失敗しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingCompletedNotification  </span> </td> 
   <td colname="2"> バッファリングが完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingStartedNotification  </span> </td> 
   <td colname="2"> メディアプレイヤーがバッファリング状態に入りました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeCompleted  </span> </td> 
   <td colname="2"> 現在再生中のメディアのオーディオトラックに対する変更が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeStarted  </span> </td> 
   <td colname="2"> 現在再生中のメディアのオーディオトラックに対する変更が開始されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemChangedNotification  </span> </td> 
   <td colname="2"> <span class="codeph"> PTMediaPlayer </span>の別の<span class="codeph"> PTMediaPlayerItem </span>が設定されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemDRMMetadataChanged  </span> </td> 
   <td colname="2"> DRMメタデータが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerMediaSelectionOptionsAvailableNotification  </span> </td> 
   <td colname="2"> 新しいサブタイトルと代替オーディオトラックがあります(<span class="codeph"> PTMediaSelectionOption </span>)。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerNewNotificationEntryAddedNotification  </span> </td> 
   <td colname="2"> 新しい<span class="codeph"> PTNotification </span>が、現在の<span class="codeph"> PTMediaPlayerItem </span>の<span class="codeph"> PTNotificationHistoryItem </span>に追加されました。これは、通知イベントが通知履歴に追加されたときです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayCompletedNotification  </span> </td> 
   <td colname="2"> メディアの再生が終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekCompletedNotification  </span> </td> 
   <td colname="2"> シークが完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekErrorNotification  </span> </td> 
   <td colname="2"> 現在のシーク操作が失敗しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekStartedNotification  </span> </td> 
   <td colname="2"> シークを開始しています。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayStartedNotification  </span> </td> 
   <td colname="2"> 再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerStatusNotification  </span> </td> 
   <td colname="2"> プレイヤーのステータスが変更されました。 使用可能なステータス値は次のとおりです。 
    <ul id="ul_DDBE8CAD5D5A46D2AAA6B98F0754A881"> 
     <li id="li_48F9AD580BCB4BB8A5C2DFED0DF9970F"> <p> <span class="codeph"> PTMediaPlayerStatusCreated  </span> </p> </li> 
     <li id="li_EDFB0765CF14422A95C9119DA3394163"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing  </span> </p> </li> 
     <li id="li_06E1576D50C646C19E88F0F14912F2C0"> <p> <span class="codeph"> PTMediaPlayerStatusInitialized  </span> </p> </li> 
     <li id="li_E8B7157B5B234DFFABC2E5BEC241AB84"> <p> <span class="codeph"> PTMediaPlayerStatusReady  </span> </p> </li> 
     <li id="li_FF2E66B390154EAA8791B4D874CC62E1"> <p> <span class="codeph"> PTMediaPlayerStatusPlaying  </span> </p> </li> 
     <li id="li_6F3306832B7642E4BEE84068383AFAF3"> <p> <span class="codeph"> PTMediaPlayerStatusPaused  </span> </p> </li> 
     <li id="li_AE579AB888954F89A7F1115CAC0655E6"> <p> <span class="codeph"> PTMediaPlayerStatusStopped  </span> </p> </li> 
     <li id="li_A4CEB39374E84B4AA4F7202E67B9BE43"> <p> <span class="codeph"> PTMediaPlayerStatusCompleted  </span> </p> </li> 
     <li id="li_C50EB9C459264641A9FF70EF901D7474"> <p> <span class="codeph"> PTMediaPlayerStatusError  </span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimeChangeNotification  </span> </td> 
   <td colname="2"> 現在の再生時間が変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimelineChangedNotification  </span> </td> 
   <td colname="2"> 現在のプレイヤーのタイムラインが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" colsep="1" rowsep="1"> <span class="codeph"> PTTimedMetadataChangedNotification  </span> </td> 
   <td colname="2"> TVSDKは、サブスクライブされた最初のタグを検出しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTTimedMetadataChangedInBackgroundNotification  </span> </td> 
   <td colname="2"> <p>サブスクライブされたタグがバックグラウンドマニフェストで識別され、そこから新しい<span class="codeph"> PTTimedMetadata </span>インスタンスが準備されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 通知のサンプルハンドラー{#section_D729C2403A234DD09596829D26882ADC}

次のコードスニペットに、通知の使用方法のいくつかを示します。

`PTMediaPlayerAdBreakKey`を使用して`PTAdBreak`インスタンスを取得します。

```
 - (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification { 
   // Fetch the PTAdBreak instance using PTMediaPlayerAdBreakKey 
   PTAdBreak *adBreak = [notification.userInfo objectForKey:PTMediaPlayerAdBreakKey]; 
   ... 
   ... 
} 
```

`subtitlesOptions`と`audioOptions`を設定：

```
 - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification \*) notification { 
   //SubtitlesOptions and audioOptions are set and accessible now. 
   NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions;  
   NSArray* audioOp tions = self.player.currentItem.audioOptions; 
   ... 
   ... 
} 
```

`PTMediaPlayerAdKey`を使用して`PTAd`インスタンスを取得します。

```
 - (void) onMediaPlayerAdPlayStarted:(NSNotification \*)  notification { 
   // Fetch the PTAdinstance using PTMediaPlayerAdKey 
   PTAd *ad = [notification.userInfo objectForKey:PTMediaPlayerAdKey]; 
   ... 
   ... 
} 
```

