---
description: プレーヤーは、プレーヤーの状態を示す様々なイベントをリッスンできます。
title: 通知の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# 通知の設定{#set-up-notifications}

プレーヤーは、プレーヤーの状態を示す様々なイベントをリッスンできます。

次のように仮定します。 `PTMediaPlayer` は、クライアントプレーヤーのプロパティです。 `self.player` 次の例では、 `PTMediaPlayer` インスタンス。 次の例では、 `addObservers` メソッドを使用します。このメソッドは、PTMediaPlayer の設定手順に示され、次の通知のほとんどを含みます。

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

## iOS通知 {#section_65D9B2DBF5574313BD3218AB02242BBB}

`ThePTMediaPlayerNotifications` クラスは、 TVSDK がプレーヤーにディスパッチする通知をリストします。

<table frame="all" colsep="1" rowsep="1" id="table_ios_notifications"> 
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>通知</b> </td> 
   <td colname="2"> <b>意味</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakCompletedNotification </span> </td> 
   <td colname="2"> 広告ブレークが終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdBreakStartedNotification </span> </td> 
   <td colname="2"> 広告ブレークが開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdClickNotification </span> </td> 
   <td colname="2"> ユーザーがバナー広告をクリックしました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdCompletedNotification </span> </td> 
   <td colname="2"> 個々の広告が終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdProgressNotification </span> </td> 
   <td colname="2"> 広告が進行しました。広告の再生中、常にディスパッチされます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerAdStartedNotification </span> </td> 
   <td colname="2"> 個々の広告が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTBackgroundManifestErrorNotification </span> </td> 
   <td colname="2"> バックグラウンドマニフェストのダウンロードに失敗しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingCompletedNotification </span> </td> 
   <td colname="2"> バッファリングが完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerBufferingStartedNotification </span> </td> 
   <td colname="2"> メディアプレーヤーがバッファリング状態に入ります。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeCompleted </span> </td> 
   <td colname="2"> 現在再生中のメディアのオーディオトラックに対する変更が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTAudioTrackChangeStarted </span> </td> 
   <td colname="2"> 現在再生中のメディアのオーディオトラックに対する変更が開始されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemChangedNotification </span> </td> 
   <td colname="2"> 別の <span class="codeph"> PTMediaPlayerItem </span> の <span class="codeph"> PTMediaPlayer </span> が設定されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerItemDRMMetadataChanged </span> </td> 
   <td colname="2"> DRM メタデータが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerMediaSelectionOptionsAvailableNotification </span> </td> 
   <td colname="2"> 新しいサブタイトルと代替オーディオトラック ( <span class="codeph"> PTMediaSelectionOption </span>) をクリックします。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerNewNotificationEntryAddedNotification </span> </td> 
   <td colname="2"> 新しい <span class="codeph"> PTNotification </span> が <span class="codeph"> PTNotificationHistoryItem </span> 現在の <span class="codeph"> PTMediaPlayerItem </span>（通知イベントが通知履歴に追加された場合）。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayCompletedNotification </span> </td> 
   <td colname="2"> メディアの再生が終了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekCompletedNotification </span> </td> 
   <td colname="2"> シークが完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekErrorNotification </span> </td> 
   <td colname="2"> 現在のシーク操作に失敗しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerSeekStartedNotification </span> </td> 
   <td colname="2"> シークを開始しています。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerPlayStartedNotification </span> </td> 
   <td colname="2"> 再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerStatusNotification </span> </td> 
   <td colname="2"> プレーヤーのステータスが変更されました。 可能なステータス値は次のとおりです。 
    <ul id="ul_DDBE8CAD5D5A46D2AAA6B98F0754A881"> 
     <li id="li_48F9AD580BCB4BB8A5C2DFED0DF9970F"> <p> <span class="codeph"> PTMediaPlayerStatusCreated </span> </p> </li> 
     <li id="li_EDFB0765CF14422A95C9119DA3394163"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing </span> </p> </li> 
     <li id="li_06E1576D50C646C19E88F0F14912F2C0"> <p> <span class="codeph"> PTMediaPlayerStatusInitialized </span> </p> </li> 
     <li id="li_E8B7157B5B234DFFABC2E5BEC241AB84"> <p> <span class="codeph"> PTMediaPlayerStatusReady </span> </p> </li> 
     <li id="li_FF2E66B390154EAA8791B4D874CC62E1"> <p> <span class="codeph"> PTMediaPlayerStatusPlaying </span> </p> </li> 
     <li id="li_6F3306832B7642E4BEE84068383AFAF3"> <p> <span class="codeph"> PTMediaPlayerStatusPaused </span> </p> </li> 
     <li id="li_AE579AB888954F89A7F1115CAC0655E6"> <p> <span class="codeph"> PTMediaPlayerStatusStopped </span> </p> </li> 
     <li id="li_A4CEB39374E84B4AA4F7202E67B9BE43"> <p> <span class="codeph"> PTMediaPlayerStatusCompleted </span> </p> </li> 
     <li id="li_C50EB9C459264641A9FF70EF901D7474"> <p> <span class="codeph"> PTMediaPlayerStatusError </span> </p> </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimeChangeNotification </span> </td> 
   <td colname="2"> 再生の現在時間が変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTMediaPlayerTimelineChangedNotification </span> </td> 
   <td colname="2"> 現在のプレーヤーのタイムラインが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" colsep="1" rowsep="1"> <span class="codeph"> PTTimedMetadataChangedNotification </span> </td> 
   <td colname="2"> TVSDK は、サブスクライブされたタグを最初に見つけました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> PTTimedMetadataChangedInBackgroundNotification </span> </td> 
   <td colname="2"> <p>サブスクライブされたタグは、バックグラウンドマニフェストで識別され、新しい <span class="codeph"> PTTimedMetadata </span> インスタンスがそのインスタンスから準備されます。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 通知用のサンプルハンドラー {#section_D729C2403A234DD09596829D26882ADC}

次のコードスニペットに、通知の使用方法の一部を示します。

を取得する `PTAdBreak` 使用するインスタンス `PTMediaPlayerAdBreakKey`:

```
 - (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification { 
   // Fetch the PTAdBreak instance using PTMediaPlayerAdBreakKey 
   PTAdBreak *adBreak = [notification.userInfo objectForKey:PTMediaPlayerAdBreakKey]; 
   ... 
   ... 
} 
```

設定 `subtitlesOptions` および `audioOptions`:

```
 - (void) onMediaPlayerItemMediaSelectionOptionsAvailable:(NSNotification \*) notification { 
   //SubtitlesOptions and audioOptions are set and accessible now. 
   NSArray* subtitlesOptions = self.player.currentItem.subtitlesOptions;  
   NSArray* audioOp tions = self.player.currentItem.audioOptions; 
   ... 
   ... 
} 
```

を取得する `PTAd` 使用するインスタンス `PTMediaPlayerAdKey`:

```
 - (void) onMediaPlayerAdPlayStarted:(NSNotification \*)  notification { 
   // Fetch the PTAdinstance using PTMediaPlayerAdKey 
   PTAd *ad = [notification.userInfo objectForKey:PTMediaPlayerAdKey]; 
   ... 
   ... 
} 
```
