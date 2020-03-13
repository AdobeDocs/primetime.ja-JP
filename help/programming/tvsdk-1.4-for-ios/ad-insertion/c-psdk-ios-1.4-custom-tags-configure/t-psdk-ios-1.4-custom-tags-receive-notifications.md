---
description: マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。
seo-description: マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。
seo-title: 時間指定メタデータ通知のリスナーの追加
title: 時間指定メタデータ通知のリスナーの追加
uuid: dcd1bd92-0617-4eab-8b06-7301aaff42f3
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 時間指定メタデータ通知のリスナーの追加 {#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。

次のイベントをリッスンして、時間指定メタデータを監視できます。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `PTTimedMetadataChangedNotification`:コンテンツの解析中に一意のサブスクライブ済みタグが識別されるたびに、TVSDKは新しいオブジェクトを準備し、こ `PTTimedMetadata` の通知をディスパッチします。

   このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生時のローカル時間、その他のデータが含まれます。

* `PTMediaPlayerTimeChangeNotification` :マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があるので、プロパティに追加のオ `TimedMetadata` ブジェクトが追加される場合が `MediaPlayerItem.timedMetadata` あります。

   このイベントは、このような場合にアプリケーションに通知します。

   次のいずれかの方法で時間指定メタデータを取得します。

   * アプリケーションを設定し、自分自身を通知のリスナーとして追加し、を使 `PTTimedMetadataChangedNotification` 用してオブジェクトを取得しま `PTTimedMetadataKey`す。

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * のプロパティ `timedMetadataCollection` にアクセスし `PTMediaPlayerItem`ます。これまでに通知されたす `PTTimedMetadata` べてのオブジェクトが含まれます。

