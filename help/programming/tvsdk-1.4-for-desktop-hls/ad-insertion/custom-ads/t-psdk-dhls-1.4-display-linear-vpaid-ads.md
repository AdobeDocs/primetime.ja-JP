---
description: TVSDKは、広告の時間におけるリニアビデオプレイヤー広告インターフェイス定義(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0にはFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。
seo-description: TVSDKは、広告の時間におけるリニアビデオプレイヤー広告インターフェイス定義(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0にはFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。
seo-title: 広告の時間にリニアVPAID広告を表示する
title: 広告の時間にリニアVPAID広告を表示する
uuid: 1f3a5426-79f5-49a1-a913-923708c09ade
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告の時間にリニアVPAID広告を表示する{#display-linear-vpaid-ads-in-an-ad-break}

TVSDKは、広告の時間におけるリニアビデオプレイヤー広告インターフェイス定義(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0にはFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。

VPAID広告を正しく表示するには、インスタンス内に広告コンテナ( `AdContainerView`)を指定する必要があ `MediaPlayerContext` ります。

VPAID広告の制限：

* VPAID広告はインタラクティブにできるので、VPAID広告には必ずしも期間が事前に定義されているわけではありません。 したがって、（広告サーバーの応答で定義される）広告の継続時間が、広告の実際の継続時間に必ずしも正確に一致するとは限りません。
* VPAID 1.0広告の場合、TVSDKは、デバイスにFlash Player 14.0.0.160以降がインストールされている必要があります。 以前のバージョンのFlash Playerでは、この機能は無効になり、VPAID 1.0広告はスキップされます。

広告の時間内にVPAID広告（バージョン1.0または2.0）を表示するための広告コンテナを設定するには：

1. 以下のサンプルコードを使用して、VPAID広告を表示できる広告コンテナを設定します。

   ```
   var context:MediaPlayerContext =  
     new MediaPlayerContext(_authorizedFeatureHelper.authorizedFeatures); 
   
   adContainer = new AdContainerView(); 
   adContainer.x = adContainer.y = 0; 
   adContainer.setSize(videoContainer.width, videoContainer.height); 
   addChild(adContainer); 
   
   context.adContainer = adContainer; 
   _player = new DefaultMediaPlayer(context);
   ```

1. ビューのサイズが変更されたら、広告コンテナのサイズをリセットします。

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >フルスクリーン変更イベントを取得し、広告コンテナに新しいサイズを設定したら、次のようにステージ表示状態を渡して、プレーヤーのサイズが正しく変更されることを確認します。   >
   >
   >
   ```>
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```   >
   >



