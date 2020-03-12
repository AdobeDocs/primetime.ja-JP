---
description: TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
seo-description: TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
seo-title: クリック可能な広告
title: クリック可能な広告
uuid: dc02cba7-34ad-4c74-9ceb-2fc1050d54aa
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# クリック可能な広告{#clickable-ads}

TVSDKは、クリックスルー広告に対して行動を起こすための情報を提供します。 プレイヤーのUIを作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK for iOSでは、リニア広告のみがクリック可能です。

## 広告のクリックに対する対応 {#section_537AF2593FDB4257B81AAE2103B0C719}

ユーザーが広告、コンパニオンバナー広告または関連ボタンをクリックした場合、アプリは応答する必要があります。 TVSDKは、クリックのリンク先URLに関する情報を提供します。

1. TVSDKのイベントリスナーを設定し、クリックスルー情報を提供するには、のオブザーバーを追加しま `PTMediaPlayerAdClickNotification`す。

   >[!NOTE]
   >
   >ユーザーが広告、コンパニオンバナー広告または関連ボタンをクリックすると、TVSDKは、クリック先に関する情報を含む、この通知をディスパッチします。

1. クリック可能な広告に対するユーザーのインタラクションを監視します。
1. ユーザーが広告またはボタンをタッチまたはクリックしたら、を使用してTVSDKに通知しま `[_player notifyClick:_currentAd.primaryAsset];`す。
1. TVSDKからイベント `PTMediaPlayerAdClickNotification` をリッスンします。
1. クリックスルーURLと関連情報を取得するには、オブジェクトを使用 `PTMediaPlayerAdClickURLKey` します。
1. ビデオを一時停止します。
1. クリックスルー情報を使用して、広告のクリックスルーURLと関連情報を表示します。

   >[!NOTE]
   >
   >例えば、次のいずれかの方法で情報を表示できます。

   * アプリケーションでクリックスルーURLをブラウザーで開きます。

      デスクトッププラットフォームでは、ビデオ広告の再生領域を使用して、ユーザーのクリック時にクリックスルーURLを呼び出します。
   * ユーザーを外部モバイルWebブラウザーにリダイレクトします。

      モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの表示と非表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別のビューを使用して、クリックスルーURLが起動されます。

1. クリックスルー情報が表示されるブラウザーウィンドウを閉じ、ビデオの再生を再開します。

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

