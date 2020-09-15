---
description: TVSDKは、広告の時間内でのリニアVideo Player-Ad Interface Definition(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0はFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。
seo-description: TVSDKは、広告の時間内でのリニアVideo Player-Ad Interface Definition(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0はFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。
seo-title: 広告の時間にリニアVPAID広告を表示する
title: 広告の時間にリニアVPAID広告を表示する
uuid: 1f3a5426-79f5-49a1-a913-923708c09ade
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# 広告の時間にリニアVPAID広告を表示する{#display-linear-vpaid-ads-in-an-ad-break}

TVSDKは、広告の時間内でのリニアVideo Player-Ad Interface Definition(VPAID)広告の表示をサポートしています。 VPAIDバージョン1.0はFlashが必要ですが、バージョン2.0はBrowser TVSDKおよびJavaScriptとも連携します。

VPAID広告を正しく表示するには、インスタンス内に広告コンテナ( `AdContainerView`)を指定する必要があり `MediaPlayerContext` ます。

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

