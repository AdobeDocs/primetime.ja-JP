---
description: TVSDK は、クリックスルー広告に対して行動できるように情報を提供します。 プレーヤー UI を作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。
title: クリック可能な広告
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# クリック可能な広告{#clickable-ads}

TVSDK は、クリックスルー広告に対して行動できるように情報を提供します。 プレーヤー UI を作成する際に、ユーザーがクリック可能な広告をクリックしたときの応答方法を決定する必要があります。

TVSDK for iOSでは、リニア広告のみがクリック可能です。

## 広告のクリック数への応答 {#section_537AF2593FDB4257B81AAE2103B0C719}

ユーザーが広告、コンパニオンバナー広告または関連ボタンをクリックした場合、アプリケーションは応答する必要があります。 TVSDK は、クリックのリンク先 URL に関する情報を提供します。

1. TVSDK 用のイベントリスナーを設定し、クリックスルー情報を提供するには、以下の監視者を追加します。 `PTMediaPlayerAdClickNotification`.

   >[!NOTE]
   >
   >ユーザーが広告、コンパニオンバナー広告または関連するボタンをクリックすると、 TVSDK は、クリックの宛先に関する情報を含め、この通知をディスパッチします。

1. クリック可能な広告に対するユーザーインタラクションを監視します。
1. ユーザーが広告やボタンをタッチまたはクリックしたら、TVSDK に通知するには、 `[_player notifyClick:_currentAd.primaryAsset];`.
1. をリッスンします。 `PTMediaPlayerAdClickNotification` イベントを TVSDK から取得します。
1. クリックスルー URL と関連情報を取得するには、 `PTMediaPlayerAdClickURLKey` オブジェクト。
1. ビデオを一時停止します。
1. クリックスルー情報を使用して、広告クリックスルー URL と関連情報を表示します。

   >[!NOTE]
   >
   >例えば、次のいずれかの方法で情報を表示できます。

   * アプリケーションで、ブラウザーでクリックスルー URL を開く。

     デスクトッププラットフォームでは、ビデオ広告の再生領域を使用して、ユーザーのクリック時にクリックスルー URL を呼び出します。
   * ユーザーを外部のモバイル Web ブラウザーにリダイレクトします。

     モバイルデバイスでは、ビデオ広告の再生領域は、コントロールの非表示と表示、再生の一時停止、フルスクリーンへの拡張など、他の機能に使用されます。 これらのデバイスでは、スポンサーボタンなどの別のビューを使用して、クリックスルー URL を起動します。

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
