---
description: PTNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーのステータスが変化する原因にもなります。
title: プレイヤーのステータス、アクティビティ、エラーおよびログの通知
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# プレイヤーの状態、アクティビティ、エラー、ログに関する通知{#notifications-for-player-status-activity-errors-and-logs-overview}

PTNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーのステータスが変化する原因にもなります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

>[!IMPORTANT]
>
>TVSDKはまた、*`notification`*&#x200B;を使用して`NSNotifications`（`PTMediaPlayer`通知） *`event`*&#x200B;通知を参照し、プレイヤーのアクティビティに関する情報を提供します。

TVSDKは、`PTNotification`を発行する際にも`PTMediaPlayerNewNotificationItemEntryNotification`を発行します。

イベントリスナーを実装して、イベントを取得し、応答します。 多くのイベントは`PTNotification`ステータス通知を提供します。

## 通知内容{#notification-content}

PTNotificationは、プレイヤーのステータスに関連する情報を提供します。

TVSDKは、`PTNotification`通知の時系列リストを提供します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`:INFO、WARNまたはERROR。
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキー/値のペア。例えば、`URL`という名前のキーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与える別の `PTNotification` オブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログ記録やグラフィカル表現のためにリモートサーバーに送信したりできます。

## 通知の設定{#notification-setup}

TVSDKは、プレイヤーに基本的な通知を設定しますが、カスタム通知に対しても同じ設定を行う必要があります。

`PTNotification`には2つの実装があります。

* リスニングするには
* カスタム通知を`PTNotificationHistory`に追加するには

通知をリッスンするために、TVSDKは`PTNotification`クラスをインスタンス化し、それを`PTMediaPlayerItem`のインスタンスに接続します。このインスタンスはPTMediaPlayerインスタンスにアタッチされます。 `PTMediaPlayer`ごとに`PTNotificationHistory`インスタンスが1つだけ存在します。

>[!IMPORTANT]
>
>カスタマイズを追加する場合は、TVSDKではなく、アプリケーションでこれらの手順を実行する必要があります。

## 通知をリッスン{#listen-to-notifications}

`PTMediaPlayer`内の`PTNotification`通知をリッスンする方法は2つあります。

1. `PTMediaPlayerItem`の`PTNotificationHistory`をタイマーで手動で確認し、違いを確認します。

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`のポストされた[NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html)を使用します。
1. 通知を取得する`PTMediaPlayer`のインスタンスを使用して`NSNotification`に登録します。

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## 通知コールバックを実装{#implement-notification-callbacks}

通知コールバックを実装できます。

1. `NSNotification`ユーザー情報から`PTNotification`を取得し、`PTMediaPlayerNotificationKey`を使用してその値を読み取ることで、通知コールバックを実装します。

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## 追加カスタム通知{#add-custom-notifications}

カスタム通知を追加するには：
新しい`PTNotification`を作成し、現在の`PTMediaPlayerItem`を使用して`PTNotificationHistory`に追加します。

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
