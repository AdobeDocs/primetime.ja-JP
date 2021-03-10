---
description: 再生が広告の時間に到達する、広告の時間を渡す、または広告の時間で終わる場合、TVSDKは、現在の再生ヘッドの位置に関するデフォルトの動作を定義します。
title: 広告の再生をカスタマイズする
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---


# 広告の再生をカスタマイズ{#customize-playback-with-ads}

再生が広告の時間に到達する、広告の時間を渡す、または広告の時間で終わる場合、TVSDKは、現在の再生ヘッドの位置に関するデフォルトの動作を定義します。

>[!TIP]
>
>デフォルトの動作は`PTAdPolicySelector`クラスを使用して上書きできます。

デフォルトの動作は、通常の再生中に広告の時間を渡すか、ビデオ内をシークするかによって異なります。

次の方法で広告再生動作をカスタマイズできます。

* ユーザーがビデオの視聴を停止した位置を保存し、以降のセッションで同じ位置で再生を再開します。
* 広告の時間がユーザーに提示された場合、ユーザーが新しい位置までシークしても、数分間は広告を何も表示しません。
* 数分後にコンテンツの再生が失敗した場合は、ストリームを再開するか、同じコンテンツの別のソースにフェイルオーバーします。

   フェイルオーバー再生セッションで、ユーザーが広告をスキップして、以前に失敗した位置に再開できるように、プリロール広告またはミッドロール広告を無効にできます。 TVSDKは、プリロール広告とミッドロール広告のスキップを有効にするメソッドを提供します。

## 広告再生用APIエレメント{#section_296ADE00CFEA40CBA1B46142720D13A5}

TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
以下のAPIエレメントは、再生のカスタマイズに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>APIエレメント</b></th> 
   <th colname="col2" class="entry"><b>広告をサポートするコンテンツ</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdMetadata  </span> </td> 
   <td colname="col2"> 広告の時間を視聴者が視聴したものとしてマークするかどうかを制御します。視聴済みの場合はマークするタイミングを制御します。 <span class="codeph"> adBreakAsWatched </span>プロパティを使用して、監視ポリシーを設定し、取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdPolicySelector  </span> </td> 
   <td colname="col2"> TVSDKの広告動作をカスタマイズできるプロトコル。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTDefaultAdPolicySelector  </span> </td> 
   <td colname="col2"> デフォルトのTVSDK動作を実装するクラス。 アプリケーションは、このクラスをオーバーライドして、完全なインターフェイスを実装せずにデフォルトの動作をカスタマイズできます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTMediaPlayer  </span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"> <span class="codeph"> localTime  </span>. <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocalTime </span> 。 <p>ここで、ストリーム内のローカル時間を基準にしてシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"> <span class="codeph"> getTimeline.convertToLocalTimeを参照して </span>ください。 <p>タイムライン上のバーチャル位置がローカル位置に変換されます。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PTAdBreak  </span> </td> 
   <td colname="col2"> <span class="codeph"> isWatched </span> プロパティビューアが広告を視聴したかどうかを示します。 </td> 
  </tr> 
 </tbody> 
</table>

## カスタマイズ再生の設定{#section_8209BAACC7814C9399988DC7DE9CF4CA}

広告動作をカスタマイズまたは上書きする前に、広告ポリシーインスタンスをTVSDKに登録します。

広告動作をカスタマイズするには、次のいずれかを実行します。

* `PTAdPolicySelector`プロトコルに準拠し、必要なポリシー選択メソッドをすべて実装します。

   デフォルトの広告動作&#x200B;**すべての**&#x200B;を上書きする必要がある場合は、このオプションをお勧めします。

* `PTDefaultAdPolicySelector`クラスをオーバーライドし、カスタマイズが必要な動作のみに実装を提供します。

   デフォルトの動作の&#x200B;**一部**&#x200B;のみを上書きする必要がある場合は、このオプションをお勧めします。

両方のオプションに対して、次のタスクを実行します。

1. TVSDKで使用するポリシーインスタンスを、クライアントファクトリを介して登録します。

   >[!NOTE]
   >
   >再生開始時に登録されるカスタム広告ポリシーは、`PTMediaPlayer`インスタンスの割り当てが解除されるとクリアされます。 新しい再生セッションが作成されるたびに、ポリシーセレクターインスタンスをアプリケーションで登録する必要があります。

   例：

   ```
   // Create an instance of the custom policy selector 
   PTS5MinuteSkipBreakPolicySelector *adPolicySelector  
        = [[[PTS5MinuteSkipBreakPolicySelector alloc] initWithMediaPlayer:self.player] autorelease]; 
   
   // register this instance 
   [[PTDefaultMediaPlayerClientFactory defaultFactory] registerAdPolicySelector:adPolicySelector];
   ```

1. カスタマイズを実装します。

## 広告の時間を一定の期間スキップ{#section_99809BE4D9BB4DEEBBF596C746CA428A}

デフォルトでは、ユーザーが広告の時間をシークオーバーすると、TVSDKは広告の時間を強制的に再生します。 この動作をカスタマイズして、前の広告の時間の完了からの経過時間が一定の分数以内である場合に、広告の時間をスキップするように設定できます。

>[!IMPORTANT]
>
>広告をスキップする内部シークがある場合、再生に若干の一時停止がある可能性があります。

以下に、カスタマイズされた広告ポリシーセレクターの例を示します。このセレクターは、ユーザーが広告の時間を視聴した後、次の5分（経過時間）に広告をスキップします。

1. TVSDKで使用するポリシーインスタンスを、クライアントファクトリを介して登録します。

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

## ビデオの位置を保存して後で再開{#section_FAE252E38CED48D4BDD38BAA4A6A20A4}

現在の再生位置をビデオ内に保存し、以降のセッションで同じ位置での再生を再開できます。

動的に挿入される広告は、ユーザーセッション間で異なるので、**を**&#x200B;スライスされた広告と共に保存した場合、以降のセッションでは別の位置が参照されます。 TVSDKは、スライスされた広告を無視して、再生位置を取得するメソッドを提供します。

1. ユーザーがビデオを終了すると、アプリケーションはビデオ内の位置を取得して保存します。

   >[!TIP]
   >
   >広告の時間は含まれません。

   広告の時間は、広告パターン、フリークエンシーキャップなどのため、セッションごとに異なる場合があります。 あるセッションでのビデオの現在時間は、将来のセッションでは異なる場合があります。 ビデオ内の位置を保存すると、アプリケーションはローカル時間を取得します。 `localTime`プロパティを使用してこの位置を読み取り、デバイス上またはサーバー上のデータベースに保存できます。

   例えば、ユーザーがビデオの20分で、この位置に5分の広告が含まれる場合、`currentTime`は1200秒で、`localTime`は900秒です。

   >[!IMPORTANT]
   >
   >ライブ/リニアストリームの場合、ローカル時間と現在時間は同じです。 この場合、`convertToLocalTime`は無効です。 VODの場合、広告が再生されても、ローカル時間は変更されません。

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

1. 前のセッションで保存した位置と同じ位置でビデオを再開するには、`seekToLocalTime`を使用します。

   >[!TIP]
   >
   >このメソッドは、ローカル時間値でのみ呼び出されます。 現在の時間でメソッドを呼び出すと、誤った動作が発生します。

   現在時間をシークするには、`seekToTime`を使用します。

1. アプリケーションが`PTMediaPlayerStatusReady`ステータス変更イベントを受け取ったら、保存済みのローカル時間をシークします。

   ```
   [self.player seekToLocalTime:CMTimeMake(900, 1) completionHandler:^(BOOL finished) { 
       [self.player play]; 
   }];
   ```

1. 広告ポリシーインターフェイスで指定した広告の時間を提供します。
1. デフォルトの広告ポリシーセレクターを拡張して、カスタム広告ポリシーセレクターを実装します。
1. `selectAdBreaksToPlay`を実装して、ユーザーに表示する必要のある広告の時間を提供する

   >[!NOTE]
   >
   >このメソッドは、ローカル時間位置より前のプリロール広告ブレークとミッドロール広告ブレークを含みます。 アプリケーションで、プリロール広告の時間を再生して指定したローカル時間に再開、ミッドロール広告の時間を再生して指定したローカル時間に再開、または広告の時間を再生しないことを決定できます。