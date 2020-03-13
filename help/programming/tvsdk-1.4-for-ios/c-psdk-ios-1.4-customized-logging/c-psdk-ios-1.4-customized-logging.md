---
description: 独自のログシステムを実装できます。
seo-description: 独自のログシステムを実装できます。
seo-title: ログのカスタマイズ
title: ログのカスタマイズ
uuid: c5bdf266-4266-4896-b6e0-47710ce64e67
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ログのカスタマイズ {#customized-logging}

独自のログシステムを実装できます。

事前定義された通知を使用してログを記録する以外に、TVSDKによって生成されたログメッセージとメッセージを使用するログシステムを実装できます。 事前定義された通知の詳細については、「通知システム [」を参照してくださ](../c-psdk-ios-1.4-notification-system/c-psdk-ios-1.4-notification-system.md)い。 これらのログを使用して、プレーヤーアプリのトラブルシューティングを行い、再生と広告のワークフローをより深く理解することができます。

カスタマイズされたログでは、の共有Singletonインスタンスを使用しま `PSDKPTLogFactory`す。このインスタンスは、複数のロガーにメッセージを記録するメカニズムを提供します。 に1つ以上のロガーを定義し、追加（登録）します `PTLogFactory`。 これにより、コンソールロガー、Webロガー、コンソール履歴ロガーなど、複数のロガーをカスタム実装で定義できます。

TVSDKは、多くのアクティビティのログメッセージを生成し、登録されたロガー `PTLogFactory` にすべて転送します。 また、アプリケーションでカスタムログメッセージを生成し、登録済みロガーにすべて転送することもできます。 各ロガーは、メッセージをフィルタリングし、適切なアクションを実行できます。

には、次の2つの実装がありま `PTLogFactory`す。

* ログをリッスンするため。
* にログを追加する場合 `PTLogFactory`。

## ログのリッスン {#listen-to-logs}

ログをリッスンするために登録するには：
1. プロトコルに従うカスタムクラスを実装しま `PTLogger`す。

   ```
   @implementation PTConsoleLogger 
   
   + (PTConsoleLogger *) consoleLogger { 
       return [[[PTConsoleLogger alloc] init] autorelease]; 
   } 
   
   - (void)logEntry:(PTLogEntry *)entry { 
       //Log the message to the console using NSLog  
       NSLog(@"[%@] %@", entry.tag, entry.message); 
   } 
   
   @end
   ```

1. ログエントリを受け取るインスタンスを登録するには、のインスタンスを次の場所 `PTLogger` に追加しま `PTLoggerFactory`す。

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

次に、タイプを使用してログをフィルタリングする例を示 `PTLogEntry` します。

```
@implementation PTConsoleLogger 
 
+ (PTConsoleLogger *) consoleLogger { 
    return [[[PTConsoleLogger alloc] init] autorelease]; 
} 
 
- (id) init { 
    self = [super init]; 
 
    if (self) { 
        self.logLevel = PTLogEntryTypeInfo; 
    } 
 
    return self; 
} 
 
- (void)logEntry:(PTLogEntry *) entry { 
    //Filtering the entry by log level  
    if (entry.type < _logLevel) { 
        return; 
    } 
 
    //Log the message to the console using NSLog NSLog(@"[%@] %@", entry.tag, entry.message); 
} 
 
@end
```

## 新しいログメッセージの追加 {#add-new-log-messages}

ログをリッスンするために登録するには：
1. 新規作成し `PTLogEntry` て次に追加しま `thePTLogFactory`す。

   手動でインスタンスを作成し `PTLogEntry` て共有インスタンスに追加す `PTLogFactory` るか、マクロの1つを使用して同じタスクを実行できます。

   マクロを使用したログの例を次に示 `PTLogDebug` します。

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
