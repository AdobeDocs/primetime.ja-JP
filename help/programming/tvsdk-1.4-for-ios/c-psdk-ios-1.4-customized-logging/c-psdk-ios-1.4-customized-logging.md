---
description: 独自のログシステムを実装できます。
title: カスタマイズされたログ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# カスタマイズされたログ {#customized-logging}

独自のログシステムを実装できます。

事前に定義された通知を使用したログ記録に加えて、TVSDK で生成されたログメッセージとメッセージを使用するログシステムを実装できます。 事前定義済みの通知について詳しくは、 [通知システム](../c-psdk-ios-1.4-notification-system/c-psdk-ios-1.4-notification-system.md). これらのログを使用して、プレーヤーアプリケーションのトラブルシューティングをおこない、再生と広告のワークフローをより深く理解することができます。

カスタマイズされたログは、 `PSDKPTLogFactory`：メッセージを複数のロガーにログ記録するメカニズムを提供します。 1 つ以上のロガーを定義し、 `PTLogFactory`. これにより、コンソールロガー、Web ロガー、コンソール履歴ロガーなど、カスタム実装で複数のロガーを定義できます。

TVSDK は、多くのアクティビティに対してログメッセージを生成し、 `PTLogFactory` は、登録されているすべてのロガーに転送されます。 また、カスタムログメッセージを生成して、登録済みのロガーにすべて転送することもできます。 各ロガーは、メッセージをフィルタリングし、適切なアクションを実行できます。

には 2 つの実装があります。 `PTLogFactory`:

* ログをリッスンするため。
* ログを `PTLogFactory`.

## ログをリッスンする {#listen-to-logs}

ログのリッスンを登録するには、次の手順を実行します。
1. プロトコルに従うカスタムクラスを実装します。 `PTLogger`:

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

1. ログエントリを受け取るインスタンスを登録するには、 `PTLogger` から `PTLoggerFactory`:

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

次に、 `PTLogEntry` 型：

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

## 新しいログメッセージを追加 {#add-new-log-messages}

ログをリッスンするように登録するには：
1. 新規作成 `PTLogEntry` をクリックし、 `thePTLogFactory`:

   手動で `PTLogEntry` をクリックし、 `PTLogFactory` 共有インスタンスを使用するか、マクロの 1 つを使用して同じタスクを実行します。

   次に、 `PTLogDebug` マクロ：

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
