---
description: PTNotification オブジェクトは、プレーヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスが変更される原因となります。
title: 通知コンテンツ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# プレーヤーのステータス、アクティビティ、エラーおよびログに関する通知 {#notifications-player-status-activity-errors-logging}

`PTNotification` オブジェクトは、プレーヤーのステータス、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーのステータスが変更される原因となります。

アプリケーションは、通知とステータス情報を取得できます。 通知情報を使用して、診断および検証用のログシステムを作成することもできます。

>[!NOTE]
>
>TVSDK は、 *`notification`* 参考にする `NSNotifications` ( `PTMediaPlayer` 通知 ) *`event`* 通知。プレーヤーのアクティビティに関する情報を提供するためにディスパッチされます。

TVSDK も問題を解決しました。 `PTMediaPlayerNewNotificationItemEntryNotification` 問題が発生した場合 `PTNotification`.

イベントリスナーを実装して、イベントをキャプチャし、それに応答します。 多くのイベントには `PTNotification` ステータスの通知。

## 通知コンテンツ {#notification-content}

`PTNotification` は、プレーヤーのステータスに関連する情報を提供します。

TVSDK は、 `PTNotification` 通知。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`：情報、警告またはエラー。
   * `code`：通知の数値表現。
   * `name`：人間が判読できる、通知の説明（SEEK_ERROR など）
   * `metadata`：通知に関する関連情報を含むキーと値のペア。 例えば、 `URL` は通知に関連する URL を示す値を提供します。

   * `innerNotification`：別のへの参照 `PTNotification` オブジェクトを直接表示します。

この情報をローカルに保存して後で分析したり、ログ記録やグラフィカル表示のためにリモートサーバーに送信したりできます。

## 通知設定 {#notification-setup}

TVSDK は、プレーヤーに基本的な通知を設定しますが、カスタム通知に対しても同じ設定を行う必要があります。

には 2 つの実装があります。 `PTNotification`:

* 聞く
* カスタム通知をに追加するには、以下を実行します。 `PTNotificationHistory`

通知をリッスンするために、 TVSDK は、 `PTNotification` クラスを作成し、それを `PTMediaPlayerItem`:PTMediaPlayer インスタンスに添付される たった一人しか無い `PTNotificationHistory` インスタンスごと `PTMediaPlayer`.

>[!IMPORTANT]
>
>カスタマイズを追加する場合は、TVSDK ではなく、アプリケーションでこれらの手順を実行する必要があります。

## 通知をリッスンする {#listen-to-notifications}

をリッスンする方法は 2 つあります。 `PTNotification` 通知 `PTMediaPlayer`:

1. 手動で `PTNotificationHistory` の `PTMediaPlayerItem` タイマーを使用して、違いを確認します。

   ```
   //Access to the PTMediaPlayerItem  
   PTMediaPlayerItem *item = self.player.currentItem; 
   PTNotificationHistory *notificationHistory = item.notificationHistory; 
   
   //Get the list of notification events from the notification History  
   NSArray *notifications = notificationHistory.notificationItems;
   ```

1. 投稿した [NSNotification](https://developer.apple.com/library/mac/%23documentation/Cocoa/Reference/Foundation/Classes/NSNotification_Class/Reference/Reference.html) の `PTMediaPlayerPTMediaPlayerNewNotificationEntryAddedNotification`.
1. に登録 `NSNotification` を使用して、 `PTMediaPlayer` 通知の取得元となるもの：

   ```
   //Register to the NSNotification 
   
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerNotification:)  
     name:PTMediaPlayerNewNotificationEntryAddedNotification object:self.player];
   ```

## 通知コールバックの実装 {#implement-notification-callbacks}

通知コールバックを実装できます。

通知コールバックを実装するには、 `PTNotification` から `NSNotification` ユーザー情報を使用し、値を読み取る `PTMediaPlayerNotificationKey`:

```
- (void) onMediaPlayerNotification:(NSNotification *) nsnotification { 
    PTNotification *notification = [nsnotification.userInfo objectForKey:PTMediaPlayerNotificationKey]; 
    NSLog(@"Notification: %@", notification); 
}
```

## カスタム通知の追加 {#add-custom-notifications}

カスタム通知を追加するには：新しい `PTNotification` をクリックし、 `PTNotificationHistory` 現在の `PTMediaPlayerItem`:

```
//Access to the PTMediaPlayerItem  
PTMediaPlayerItem *item = self.player.currentItem; 
PTNotificationHistory *notificationHistory = item.notificationHistory; 
 
//Create notification 
PTNotification* notification = [[PTNotification notificationWithType:PTNotificationTypeWarning code:99999 description:@"Custom notification description"]; 
 
//Add notification 
[notificationHistory addNotification:notification];
```
