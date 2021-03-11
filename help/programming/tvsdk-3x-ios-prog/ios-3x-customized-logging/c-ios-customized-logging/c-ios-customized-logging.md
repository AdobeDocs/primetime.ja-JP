---
description: 独自のログシステムを実装できます。
title: カスタマイズされたログの理解
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# カスタマイズされたログ{#customized-logging}

独自のログシステムを実装できます。

事前定義済みの通知を使用したログ記録に加えて、TVSDKで生成されたログメッセージとメッセージを使用するログシステムを実装できます。 事前定義済みの通知について詳しくは、[通知システム](https://help.adobe.com/en_US/primetime/psdk/ios/index.html#PSDKs-concept-The_Notification_System)を参照してください。 これらのログを使用して、プレーヤーアプリのトラブルシューティングを行い、再生と広告のワークフローをより深く理解することができます。

カスタマイズされたログでは、`PSDKPTLogFactory`の共有シングルトンインスタンスを使用します。このインスタンスは、メッセージを複数のロガーに記録するメカニズムを提供します。 `PTLogFactory`に1つ以上のロガーを定義して追加（登録）します。 これにより、コンソールロガー、Webロガー、コンソール履歴ロガーなど、複数のロガーをカスタム実装に定義できます。

TVSDKは、多くのアクティビティに対してログメッセージを生成し、`PTLogFactory`が登録済みロガーにすべて転送します。 また、カスタムログメッセージを生成して、登録済みロガーにすべて転送することもできます。 各ロガーはメッセージをフィルタリングし、適切なアクションを実行できます。

`PTLogFactory`には2つの実装があります。

* ログをリッスンするため。
* `PTLogFactory`にログを追加する場合。

## ログをリッスン{#listen-to-logs}

ログをリッスンするための登録を行うには：
1. プロトコル`PTLogger`に続くカスタムクラスを実装します。

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

1. ログエントリを受け取るインスタンスを登録するには、`PTLogger`のインスタンスを`PTLoggerFactory`に追加します。

   ```
   PTConsoleLogger *logger = [PTConsoleLogger consoleLogger]; 
   // Either use the addLogger method: 
   [[PTLogFactory sharedInstance] addLogger:(logger)] 
   
   //Or replace the preceding line with this macro for ease of use 
   //PTLogAddLogger(logger); 
   ```

<!--<a id="example_3738B5A8B4C048D28695E62297CF39E3"></a>-->

次に、`PTLogEntry`型を使用してログをフィルタリングする例を示します。

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

## 追加新しいログメッセージ{#add-new-log-messages}

ログをリッスンするために登録するには：

新しい`PTLogEntry`を作成し、`thePTLogFactory`に追加します。

`PTLogEntry`を手動でインスタンス化して`PTLogFactory`共有インスタンスに追加するか、マクロの1つを使用して同じタスクを実行できます。

`PTLogDebug`マクロを使用したログの例を次に示します。

<!--<a id="example_F014436E1686468F941F4EBD1A21B18E"></a>-->

```
// The following line creates an instance of PTLogEntry with type PTLogEntryDebug, 
// tag "DEBUG_PLAYBACK", and message "Playback has started". 
// Then the PTLogEntry is automatically added to the PTLogFactory  
 
PTLogDebug(@"[DEBUG_PLAYBACK] Playback has started");
```
