---
description: TVSDKは、広告の時間内でのリニアVideo Player-Ad Interface Definition(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0はFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。
title: 広告の時間にリニアVPAID広告を表示する
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# 広告の時間{#display-linear-vpaid-ads-in-an-ad-break}にリニアVPAID広告を表示

TVSDKは、広告の時間内でのリニアVideo Player-Ad Interface Definition(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0はFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。

VPAID広告を正しく表示するには、`MediaPlayerContext`インスタンス内に広告コンテナ(`AdContainerView`)を指定する必要があります。

VPAID広告の制限事項：

* VPAID広告はインタラクティブにできるので、VPAID広告には必ずしも継続時間が事前に定義されているわけではありません。 したがって、広告の継続時間（広告サーバーの応答で定義）は、広告の真の継続時間に必ずしも正確に対応しているとは限りません。
* VPAID 1.0広告の場合、TVSDKは、Flashプレイヤー14.0.0.160以降がデバイスにインストールされている必要があります。 以前のバージョンのFlashプレーヤーでは、この機能は無効になり、VPAID 1.0広告はスキップされます。

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

1. 表示のサイズが変更されたら、広告コンテナのサイズをリセットします。

   ```
   adContainer.setSize(stage.stageWidth, stage.stageHeight);
   ```

   >[!NOTE]
   >
   >フルスクリーン変更イベントを取得し、広告コンテナに新しいサイズを設定したら、次のようにステージ表示状態を渡して、プレイヤーのサイズが正しく変更されるようにします。
   >
   >
   ```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```

