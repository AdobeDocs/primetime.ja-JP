---
description: 再生が広告の時間に到達する、広告の時間を渡す、または広告の時間で終わると、TVSDKは、現在の再生ヘッドの位置に関するデフォルトの動作を定義します。
seo-description: 再生が広告の時間に到達する、広告の時間を渡す、または広告の時間で終わると、TVSDKは、現在の再生ヘッドの位置に関するデフォルトの動作を定義します。
seo-title: 広告の再生のカスタマイズ
title: 広告の再生のカスタマイズ
uuid: 58002ec2-65ab-4e3b-8e3b-f755ced5cb5a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告の再生のカスタマイズ{#customize-playback-with-ads}

再生が広告の時間に到達する、広告の時間を渡す、または広告の時間で終わると、TVSDKは、現在の再生ヘッドの位置に関するデフォルトの動作を定義します。

>[!TIP]
>
>クラスを使用して、デフォルトの動作を上書きで `PTAdPolicySelector` きます。

デフォルトの動作は、通常の再生中に広告の時間を渡すか、ビデオ内でのシークによって異なります。

次の方法で広告再生動作をカスタマイズできます。

* ユーザーがビデオの視聴を停止した位置を保存し、以降のセッションで同じ位置で再生を再開します。
* 広告の時間がユーザーに表示される場合は、ユーザーが新しい位置までシークしても、数分間、追加の広告は表示されません。
* 数分後にコンテンツの再生に失敗した場合は、ストリームを再開するか、同じコンテンツの別のソースにフェイルオーバーします。

   フェイルオーバー再生セッションで、ユーザーが広告をスキップして前回失敗した位置に再開できるように、プリロール広告またはミッドロール広告を無効にできます。 TVSDKは、プリロール広告とミッドロール広告のスキップを有効にするメソッドを提供します。

## 広告再生用のAPI要素 {#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
次のAPI要素は、再生のカスタマイズに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API要素 </th> 
   <th colname="col2" class="entry"> 広告をサポートするコンテンツ </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata </span> </td> 
   <td colname="col2"> 広告の時間を、視聴者が視聴済みとしてマークするかどうか、およびマークするタイミングを制御します。 adBreakAsWatchedプロパティを使用して、監視ポリシーを設 <span class="codeph"> 定および取 </span> 得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector </span> </td> 
   <td colname="col2"> TVSDKの広告動作をカスタマイズできるプロトコル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector </span> </td> 
   <td colname="col2"> デフォルトのTVSDK動作を実装するクラス。 アプリケーションは、このクラスをオーバーライドして、完全なインターフェイスを実装せずにデフォルトの動作をカスタマイズできます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime </span>. <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocalTime </span> . <p>ここでは、ストリーム内のローカル時間を基準にしてシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTimeを参照してくださ </span>い。 <p>タイムライン上のバーチャル位置がローカル位置に変換されます。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatchedプロ </span> パティ。 ビューアが広告を視聴したかどうかを示します。 </td> 
  </tr> 
 </tbody> 
</table>

## カスタマイズされた再生の設定 {#section_8209BAACC7814C9399988DC7DE9CF4CA}

広告の動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをTVSDKに登録します。

動作をカスタマイズするには、次のいずれかの操作を行います。

* プロトコルに準拠し `PTAdPolicySelector` 、必要なポリシー選択方法をすべて実装します。

   すべてのデフォルトの広告動作を上書きする必要がある場合 **は** 、このオプションをお勧めします。

* クラスをオーバ `PTDefaultAdPolicySelector` ーライドし、カスタマイズが必要な動作のみを実装します。

   このオプションは、一部のデフォルトの動作のみを上書きする **必要が** ある場合に推奨されます。

両方のオプションに対して、次のタスクを実行します。

1. TVSDKが使用するポリシーインスタンスを、クライアントファクトリを通じて登録します。

   >[!NOTE]
   >
   >再生の開始時に登録されたカスタム広告ポリシーは、インスタンスの割り当てが解除され `PTMediaPlayer` るとクリアされます。 新しい再生セッションが作成されるたびに、アプリケーションでポリシーセレクターインスタンスを登録する必要があります。

   例：

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. カスタマイズを実装します。

## 広告の時間を一定期間スキップ {#section_99809BE4D9BB4DEEBBF596C746CA428A}

デフォルトでは、TVSDKは、ユーザーが広告の時間をシークオーバーすると、広告の時間を強制的に再生します。 前の時間の完了からの経過時間が一定の分数以内である場合、広告の時間をスキップする動作をカスタマイズできます。

>[!IMPORTANT]
>
>内部シークがあって広告をスキップする場合、再生が少し停止する場合があります。

次の例では、カスタマイズされた広告ポリシーセレクターを使用して、ユーザーが広告の時間を視聴した後、次の5分（時間枠）で広告をスキップします。

1. TVSDKが使用するポリシーインスタンスを、クライアントファクトリを通じて登録します。

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

現在の再生位置をビデオに保存し、今後のセッションで同じ位置での再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、スライスされた広告 **での** 「位置」を保存すると、将来のセッションでは別の位置が参照されます。 TVSDKは、スライスされた広告を無視して再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得し、保存します。

   >[!TIP]
   >
   >広告の時間は含まれません。

   広告の時間は、広告パターンや周波数制限などによって、セッションごとに異なる場合があります。 あるセッションでのビデオの現在時間は、今後のセッションで異なる場合があります。 ビデオ内の位置を保存すると、アプリケーションはローカル時間を取得します。 この位置を読 `localTime` み取るには、このプロパティを使用します。この位置は、デバイス上またはサーバー上のデータベース内に保存できます。

   例えば、ユーザーがビデオの20分目にいて、この位置に5分の広告が含まれている場合、 `currentTime` 1,200秒で、この位置に `localTime` は900秒です。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームの場合、ローカル時間と現在時間は同じです。 この場合、は何も `convertToLocalTime` 影響しません。 VODの場合、広告の再生中、ローカル時間は変更されません。

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

1. ビデオを同じ位置で再開するには：前のセッションで保存した位置からビデオの再生を再開するには、 `seekToLocalTime`

   >[!TIP]
   >
   >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間でメソッドを呼び出すと、誤った動作が発生します。

   現在の時間をシークするには、を使用しま `seekToTime`す。

1. アプリケーションがステータス変更イ `PTMediaPlayerStatusReady` ベントを受け取ったら、保存されたローカル時間をシークします。

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. 広告ポリシーインターフェイスで指定した広告の時間を提供します。
1. デフォルトの広告ポリシーセレクターを拡張して、カスタム広告ポリシーセレクターを実装します。
1. 実装することでユーザーに表示する必要がある広告の時間を提供する `selectAdBreaksToPlay`

   >[!NOTE]
   >
   >この方法には、プリロール広告の時間と、ローカル時間の位置より前のミッドロール広告の時間が含まれます。 アプリケーションで、プリロール広告の時間を再生して指定したローカル時間に再開する、ミッドロール広告の時間を再生して指定したローカル時間に再開する、または広告の時間を再生しないことを決定できます。

