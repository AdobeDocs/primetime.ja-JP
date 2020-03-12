---
description: PTNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。
seo-description: PTNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。
seo-title: プレイヤーのステータス、アクティビティ、エラーおよびログの通知
title: プレイヤーのステータス、アクティビティ、エラーおよびログの通知
uuid: 59716a66-3736-4076-8011-8104bfe3a83a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# プレイヤーのステータス、アクティビティ、エラーおよびログに関する通知 {#notifications-for-player-status-activity-errors-and-logs-overview}

PTNotificationオブジェクトは、プレイヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスの変更の原因にもなります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

>[!IMPORTANT]
>
>また、TVSDKは、プレイヤ *`notification`* ーアクティビティに関する情 `NSNotifications` 報を提供するためにディスパッチされる( `PTMediaPlayer`*`event`* 通知)通知を参照するためにも使用します。

また、TVSDKは、問題が発生し `PTMediaPlayerNewNotificationItemEntryNotification` た場合にも問題を発生させま `PTNotification`す。

イベントリスナーを実装して、イベントを取得し、イベントに応答します。 多くのイベントは、ステータス `PTNotification` 通知を提供します。

## 通知内容 {#notification-content}

PTNotificationは、プレイヤーのステータスに関連する情報を提供します。

TVSDKは、通知の時系列のリストを提供 `PTNotification` します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`:INFO、WARNまたはERROR。
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキーと値のペア。 例えば、という名前のキ `URL` ーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与え `PTNotification` る別のオブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログやグラフィカル表示のためにリモートサーバーに送信したりできます。

## 通知の設定 {#notification-setup}

TVSDKは、基本通知用にプレイヤーを設定しますが、カスタム通知用にも同じ設定を行う必要があります。

には、次の2つの実装がありま `PTNotification`す。

* 聞く
* カスタム通知を `PTNotificationHistory`

通知をリッスンするために、TVSDKはクラスをイ `PTNotification` ンスタンス化し、PTMediaPlayerインスタンスにアタッチさ `PTMediaPlayerItem`れる、クラスのインスタンスに添付します。 1つのインスタンスにつ `PTNotificationHistory` き1つのみがあ `PTMediaPlayer`る。

>[!IMPORTANT]
>
>カスタマイズを追加する場合は、TVSDKではなく、アプリケーションでこれらの手順を実行する必要があります。

## 通知のリッスン {#listen-to-notifications}

で通知をリッスンする方法は2 `PTNotification` つあります `PTMediaPlayer`。

1. タイマーを使用し `PTNotificationHistory` てのを手 `PTMediaPlayerItem` 動で確認し、違いを確認します。

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. NSNotificationのポスト [を使](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) 用します `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`。
1. 通知の取得元 `NSNotification` のインスタンスを使用 `PTMediaPlayer` して、に登録します。

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## 通知コールバックの実装 {#implement-notification-callbacks}

通知コールバックを実装できます。

1. 次を使用して、ユーザー情報から `PTNotification` を取得し、 `NSNotification` その値を読み取ることで、通知コールバックを実装しま `PTMediaPlayerNotificationKey`す。

   ```
   - (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
       PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
       NSLog(@"Notification: %@", notification); 
   }
   ```

## カスタム通知の追加 {#add-custom-notifications}

カスタム通知を追加するには：新しいを作成 `PTNotification``PTNotificationHistory``PTMediaPlayerItem`し、現在の

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
