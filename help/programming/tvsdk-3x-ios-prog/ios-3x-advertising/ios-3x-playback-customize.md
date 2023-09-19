---
description: 再生が広告の時間に到達したとき、広告の時間を渡すとき、または広告の時間で終わるとき、 TVSDK は現在の再生ヘッドの位置に関するデフォルトの動作を定義します。
title: 広告の再生をカスタマイズする
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# 広告の再生をカスタマイズする {#customize-playback-with-ads}

再生が広告の時間に到達したとき、広告の時間を渡すとき、または広告の時間で終わるとき、 TVSDK は現在の再生ヘッドの位置に関するデフォルトの動作を定義します。

>[!TIP]
>
>デフォルトの動作は、 `PTAdPolicySelector` クラス。

デフォルトの動作は、通常の再生中に広告の時間を渡すか、ビデオでのシークによって異なります。

広告の再生動作は、次の方法でカスタマイズできます。

* ユーザーがビデオの視聴を中断した位置を保存し、以降のセッションで同じ位置で再生を再開します。
* ユーザーに広告の時間が提示される場合、ユーザーが新しい位置に移動しようとしても、追加の広告を数分間表示しません。
* 数分後にコンテンツの再生が失敗した場合は、ストリームを再起動するか、同じコンテンツの別のソースにフェイルオーバーします。

  フェールオーバー再生セッションで、ユーザーが広告をスキップして前の失敗した位置に戻るのを許可するには、プリロール広告やミッドロール広告を無効にできます。 TVSDK は、プリロール広告とミッドロール広告のスキップを有効にするメソッドを提供します。

## 広告再生用の API 要素 {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDK は、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
次の API 要素は、再生をカスタマイズするのに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>API 要素</b></th> 
   <th colname="col2" class="entry"><b>広告をサポートするコンテンツ</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> 広告の時間を、閲覧者が視聴済みとしてマークするかどうか、およびマークする場合はマークするタイミングを制御します。 次を使用して監視ポリシーを設定および取得します。 <span class="codeph"> adBreakAsWatched </span> プロパティ。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> TVSDK の広告動作をカスタマイズできるプロトコル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> デフォルトの TVSDK 動作を実装するクラス。 アプリケーションは、このクラスを上書きして、完全なインターフェイスを実装することなく、デフォルトの動作をカスタマイズできます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocalTime </span> . <p>ここでは、ストリーム内のローカル時間を基準にしたシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTime </span>. <p>タイムライン上の仮想位置がローカル位置に変換されます。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched </span> プロパティ。 閲覧者が広告を視聴したかどうかを示します。 </td> 
  </tr> 
 </tbody> 
</table>

## カスタマイズされた再生の設定 {#section_8209BAACC7814C9399988DC7DE9CF4CA}

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスを TVSDK に登録します。

広告の動作をカスタマイズするには、次のいずれかの操作を行います。

* に準拠 `PTAdPolicySelector` プロトコルを使用し、必要なすべてのポリシー選択メソッドを実装します。

  このオプションは、 **すべて** デフォルトの広告の動作です。

* 次を上書き： `PTDefaultAdPolicySelector` クラスを作成し、カスタマイズが必要な動作に対してのみ実装を提供します。

  このオプションは、 **some** のデフォルトの動作を設定します。

両方のオプションについて、次のタスクを実行します。

1. TVSDK が使用するポリシーインスタンスを、クライアントファクトリを通じて登録します。

   >[!NOTE]
   >
   >再生開始時に登録されるカスタム広告ポリシーは、 `PTMediaPlayer` インスタンスの割り当てが解除されました。 新しい再生セッションが作成されるたびに、アプリケーションはポリシーセレクターインスタンスを登録する必要があります。

   例：

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. カスタマイズ機能を実装します。

## 一定期間広告の時間をスキップ {#section_99809BE4D9BB4DEEBBF596C746CA428A}

デフォルトでは、 TVSDK は、ユーザーが広告の時間をシークオーバーする際に、広告の時間を強制的に再生します。 動作をカスタマイズして、前のブレーク完了からの経過時間が一定の分数以内の場合に、広告ブレークをスキップすることができます。

>[!IMPORTANT]
>
>広告をスキップする内部シークがある場合、再生で少し一時停止が発生している可能性があります。

次に、カスタマイズされた広告ポリシーセレクターの例では、ユーザーが広告の時間を視聴した後、5 分（ウォール時刻）以内に広告をスキップします。

1. TVSDK が使用するポリシーインスタンスを、クライアントファクトリを通じて登録します。

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. カスタマイズを実装します。

**PTS5MinuteSkipBreakPolicySelector.h**

```
#import "PTMediaPlayerNotifications.h" 
#import "PTMediaPlayer.h" 
#import "PTDefaultAdPolicySelector.h" 
 
//  extend the default policy  
selector@interface PTS5MinuteSkipBreakPolicySelector : PTDefaultAdPolicySelector 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player; 
  
@end
```

**PTS5MinuteSkipBreakPolicySelector.m**

```
#import "PTS5MinuteSkipBreakPolicySelector.h" 
  
double MIN_BREAK_INTERVAL  = 60 * 5; // 5 minutes 
  
@implementation PTS5MinuteSkipBreakPolicySelector 
{ 
    PTMediaPlayer *_player; 
    NSTimeInterval _lastAdBreakPlayedTime; 
} 
  
- (id)initWithMediaPlayer:(PTMediaPlayer *)player 
{ 
    if (self = [super init]) 
    { 
        _lastAdBreakPlayedTime = 0; 
        _player = [player retain]; 
        [self addobservers]; 
    } 
    
    return self; 
} 
  
- (NSArray *)selectAdBreaksToPlay:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectAdBreaksToPlay (%f): %f", self,  
        CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectAdBreaksToPlay:info]; 
    } 
    
    return nil; 
} 
  
- (PTAdBreakPolicyType)selectPolicyForAdBreak:(PTAdPolicyInfo *)info 
{ 
    NSLog(@"%@ - selectPolicyForAdBreak (%f): %f  %f", self,  
            CMTimeGetSeconds(info.currentTime), _lastAdBreakPlayedTime,  
            [[NSDate date] timeIntervalSince1970]); 
    
    BOOL shouldPlay = [self shouldPlayAdBreaks]; 
    if (shouldPlay) 
    { 
        return [super selectPolicyForAdBreak:info]; 
    } 
    
    return PTAdBreakPolicyTypeSkip; 
} 
  
- (BOOL)shouldPlayAdBreaks 
{ 
    NSTimeInterval currentTime = [[NSDate date] timeIntervalSince1970]; 
    if (_lastAdBreakPlayedTime <= 0) 
    { 
        return YES; 
    } 
    
    if (_lastAdBreakPlayedTime > 0 && (currentTime - _lastAdBreakPlayedTime) > MIN_BREAK_INTERVAL) 
    { 
        return YES; 
    } 
    
    // don't play any ad break if 5 minutes hasn't elapsed 
    return NO; 
} 
  
- (void) onMediaPlayerAdBreakStarted:(NSNotification *) notification 
{ 
    NSLog(@"%@ - AdBreak Start", self); 
} 
  
- (void) onMediaPlayerAdBreakCompleted:(NSNotification *) notification 
{ 
    _lastAdBreakPlayedTime = [[NSDate date] timeIntervalSince1970]; 
    NSLog(@"%@ - AdBreak Complete at: %f", self, _lastAdBreakPlayedTime); 
} 
  
- (void)addobservers 
{ 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakStarted:)  
                name:PTMediaPlayerAdBreakStartedNotification object:_player]; 
    [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdBreakCompleted:)  
                name:PTMediaPlayerAdBreakCompletedNotification object:_player]; 
} 
  
- (void)removeObservers 
{ 
    [[NSNotificationCenter defaultCenter] removeObserver:self]; 
} 
  
- (void)dealloc 
{ 
    [self removeObservers]; 
    [_player release]; 
    [super dealloc]; 
} 
  
@end
```

## ビデオの位置を保存し、後で再開します {#section_FAE252E38CED48D4BDD38BAA4A6A20A4}

ビデオの現在の再生位置を保存し、後のセッションで同じ位置で再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、位置を保存します **次を使用** スプライスされた広告は、将来のセッションでの異なる位置を指します。 TVSDK は、スライスされた広告を無視して再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得して保存します。

   >[!TIP]
   >
   >広告の期間は含まれません。

   広告の時間は、広告パターンや頻度キャップなどによって、セッションごとに異なる場合があります。 あるセッションでのビデオの現在の時刻は、将来のセッションで異なる場合があります。 ビデオ内の位置を保存する際に、アプリケーションはローカル時間を取得します。 以下を使用します。  `localTime` プロパティを使用してこの位置を読み取ることができます。この位置は、デバイス上またはサーバー上のデータベースに保存できます。

   例えば、ユーザーがビデオの 20 分目にいて、この位置に 5 分の広告が含まれている場合、 `currentTime` は 1200 秒ですが、 `localTime` この位置は 900 秒です。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームのローカル時間と現在時間は同じです。 この場合、 `convertToLocalTime` 効果はありません。 VOD の場合、広告が再生される間、ローカル時間は変更されません。

   ```
   - (void) onMediaPlayerTimeChange:(NSNotification *)notification { 
       CMTimeRange seekableRange = self.player.seekableRange; 
   
       if (CMTIMERANGE_IS_VALID(seekableRange)) { 
           double seekableRangeStart = CMTimeGetSeconds(seekableRange.start); 
           double seekableRangeDuration = CMTimeGetSeconds(seekableRange.duration); 
           double currentTime = CMTimeGetSeconds(self.player.currentTime); // includes ads 
           double localTime = CMTimeGetSeconds(self.player.localTime); // no ads 
       } 
   }
   ```

1. 前のセッションで保存した位置でビデオを再開するには、 `seekToLocalTime`.

   >[!TIP]
   >
   >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間の結果でメソッドを呼び出した場合、誤った動作が発生します。

   現在の時間をシークするには、 `seekToTime`.

1. アプリケーションが `PTMediaPlayerStatusReady` ステータス変更イベント。保存されたローカル時間をシークします。

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. 広告ポリシーインターフェイスで指定した広告の時間を提供します。
1. デフォルトの広告ポリシーセレクターを拡張して、カスタム広告ポリシーセレクターを実装します。
1. を実装してユーザーに提示する必要がある広告の時間を提供する `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >このメソッドは、ローカル時間の位置より前のプリロール広告ブレークとミッドロール広告ブレークを含みます。 アプリケーションで、プリロール広告ブレークを再生し、指定したローカル時間に再開する、ミッドロール広告ブレークを再生して指定したローカル時間に再開する、または広告ブレークを再生しない、のいずれかを決定できます。
