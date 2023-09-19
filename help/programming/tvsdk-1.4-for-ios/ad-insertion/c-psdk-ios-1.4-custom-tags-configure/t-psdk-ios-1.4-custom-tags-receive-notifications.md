---
description: マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。
title: 時間指定メタデータ通知のリスナーを追加する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# 時間指定メタデータ通知のリスナーを追加する {#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。

時間指定メタデータを監視するには、次のイベントをリッスンします。このイベントは、関連するアクティビティをアプリケーションに通知します。

* `PTTimedMetadataChangedNotification`：コンテンツの解析中に一意のサブスクライブ済みタグが識別されるたびに、 TVSDK は新しい `PTTimedMetadata` オブジェクトを選択し、この通知をディスパッチします。

  オブジェクトには、購読したタグの名前、このタグが表示される再生中のローカル時間、その他のデータが含まれます。

* `PTMediaPlayerTimeChangeNotification` ：マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストに追加のカスタムタグが表示される可能性があります。そのため、追加の `TimedMetadata` オブジェクトが `MediaPlayerItem.timedMetadata` プロパティ。

  このイベントは、このような状況が発生した場合にアプリケーションに通知します。

  次のいずれかの方法で、時間指定メタデータを取得します。

   * 自分自身をリスナーとしてに追加するアプリケーションを `PTTimedMetadataChangedNotification` 通知を送信し、次を使用してオブジェクトを取得します。 `PTTimedMetadataKey`.

     ```
     [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
       name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
     
     - (void) onTimedMetadataChanged:(NSNotification *) notification { 
         NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
         PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
     }
     ```

   * 次にアクセス： `timedMetadataCollection` のプロパティ `PTMediaPlayerItem`( すべての `PTTimedMetadata` これまでに通知されたオブジェクト。
