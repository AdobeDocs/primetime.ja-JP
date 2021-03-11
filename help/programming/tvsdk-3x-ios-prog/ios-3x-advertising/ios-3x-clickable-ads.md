---
description: TVSDKは、クリックスルー広告に対してアクションを実行できるように情報を提供します。 プレイヤーUIを作成する際、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
title: クリック可能な広告
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# クリック可能な広告{#clickable-ads}

TVSDKは、クリックスルー広告に対してアクションを実行できるように情報を提供します。 プレイヤーUIを作成する際、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK for iOSでは、リニア広告のみがクリック可能です。

## 広告のクリックに反応{#section_537AF2593FDB4257B81AAE2103B0C719}

ユーザーが広告、コンパニオンバナー広告または関連ボタンをクリックした場合、アプリケーションは応答する必要があります。 TVSDKは、クリック時のリンク先URLに関する情報を提供します。

1. TVSDKのイベントリスナーを設定し、クリックスルー情報を提供するには、`PTMediaPlayerAdClickNotification`のオブザーバーを追加します。

   >[!NOTE]
   >
   >ユーザーが広告、コンパニオンバナー広告または関連ボタンをクリックすると、TVSDKは、クリックの移動先に関する情報を含む、この通知をディスパッチします。

1. クリック可能な広告に対するユーザーの操作を監視します。
1. ユーザーが広告やボタンをタッチまたはクリックしたら、TVSDKに通知するために`[_player notifyClick:_currentAd.primaryAsset];`を使用します。
1. TVSDKの`PTMediaPlayerAdClickNotification`イベントをリッスンします。
1. クリックスルーURLと関連情報を取得するには、`PTMediaPlayerAdClickURLKey`オブジェクトを使用します。
1. ビデオを一時停止します。
1. クリックスルー情報を使用して、広告のクリックスルーURLと関連情報を表示します。

   >[!NOTE]
   >
   >例えば、次のいずれかの方法で情報を表示できます。

   * アプリケーションで、ブラウザーでクリックスルーURLを開きます。

      デスクトッププラットフォームでは、ビデオ広告の再生領域は、ユーザーがクリックするとクリックスルーURLを呼び出すのに使用されます。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      携帯端末では、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡大など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別の表示を使用して、クリックスルーURLを起動します。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じて、ビデオの再生を再開します。

   例：

   ```
      // Listening for click notification  
   [[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(onMediaPlayerAdClick:)  
    name:PTMediaPlayerAdClickNotification object:self.player]; 
   - (void) onMediaPlayerAdClick:(NSNotification *) notification { 
      NSString *url = [notification.userInfo objectForKey:PTMediaPlayerAdClickURLKey];  
      if (url != nil) { 
          [self openBrowser:[NSURL URLWithString:url]]; 
      } 
   } 
   ```
