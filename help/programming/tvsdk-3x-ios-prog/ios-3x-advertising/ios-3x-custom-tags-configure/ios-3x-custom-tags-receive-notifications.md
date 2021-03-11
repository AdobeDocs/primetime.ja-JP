---
description: マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。
title: 時間指定メタデータ追加通知のリスナー
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 時間指定メタデ追加ータ通知のリスナー{#add-listeners-for-timed-metadata-notifications}

マニフェスト内のタグに関する通知を受け取るには、適切な通知リスナーを実装します。

関連するアクティビティをアプリケーションに通知する次のイベントをリッスンすると、時間指定メタデータを監視できます。

* `PTTimedMetadataChangedNotification`:TVSDKは、コンテンツの解析中に一意のサブスクライブ済みタグを識別するたびに、新しい `PTTimedMetadata` オブジェクトを準備し、この通知をディスパッチします。

   このオブジェクトには、サブスクライブしたタグの名前、このタグが表示される再生中のローカル時間、その他のデータが含まれます。

* `PTMediaPlayerTimeChangeNotification` :マニフェスト/プレイリストが定期的に更新されるライブ/リニアストリームの場合、更新されたプレイリスト/マニフェストにカスタムタグが追加される場合があるので、追加の `TimedMetadata` オブジェクトが `MediaPlayerItem.timedMetadata` プロパティに追加される可能性があります。

   このイベントは、このような状況が発生した場合にアプリケーションに通知します。

   次のいずれかの方法で、時間指定メタデータを取得します。

   * アプリケーション自体をリスナーとして`PTTimedMetadataChangedNotification`通知に追加するように設定し、`PTTimedMetadataKey`を使用してオブジェクトを取得します。

      ```
      [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onTimedMetadataChanged:)  
        name:PTTimedMetadataChangedNotification object:self.player.currentItem]; 
      
      - (void) onTimedMetadataChanged:(NSNotification *) notification { 
          NSDictionary *timedMetadataUserInfo = [[NSDictionary alloc]initWithDictionary: notification.userInfo]; 
          PTTimedMetadata *newTimedMetadata = [timedMetadataUserInfo objectForKey: PTTimedMetadataKey]; 
      }
      ```

   * `PTMediaPlayerItem`の`timedMetadataCollection`プロパティにアクセスします。これは、これまでに通知されたすべての`PTTimedMetadata`オブジェクトで構成されます。