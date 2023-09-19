---
description: TVSDK は、広告の時間でのリニアビデオプレーヤー — 広告インターフェイス定義 (VPAID) 広告の表示をサポートしています。 VPAID バージョン 1.0 にはFlashが必要ですが、バージョン 2.0 は Browser TVSDK および JavaScript とも連携します。
title: 広告ブレークでのリニア VPAID 広告の表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 広告ブレークでのリニア VPAID 広告の表示{#display-linear-vpaid-ads-in-an-ad-break}

TVSDK は、広告の時間でのリニアビデオプレーヤー — 広告インターフェイス定義 (VPAID) 広告の表示をサポートしています。 VPAID バージョン 1.0 にはFlashが必要ですが、バージョン 2.0 は Browser TVSDK および JavaScript とも連携します。

VPAID 広告を正しく表示するには、広告コンテナ ( `AdContainerView`) を `MediaPlayerContext` インスタンス。

VPAID 広告の制限事項：

* VPAID 広告はインタラクティブにできるので、事前に定義された期間とは限りません。 したがって、広告の時間（広告サーバーの応答で定義）は、広告の真の時間に必ずしも正確に対応していない場合があります。
* VPAID 1.0 広告の場合、 TVSDK には、デバイスにFlashプレーヤー 14.0.0.160 以降がインストールされている必要があります。 以前のバージョンのFlashプレーヤーでは、この機能は無効になり、VPAID 1.0 広告はスキップされます。

広告ブレーク内に VPAID 広告（バージョン 1.0 または 2.0）を表示するための広告コンテナを設定するには：

1. 以下のサンプルコードを使用して、VPAID 広告を表示できる広告コンテナを設定します。

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
   >フルスクリーン変更イベントを取得し、広告コンテナで新しいサイズを設定したら、次のようにステージの表示状態を渡して、プレーヤーのサイズが正しく変更されるようにします。
   >
   >```
   >private function onFullScreenChange(event:FullScreenEvent):void { 
   >if (_adContainer) 
   >{ _adContainer.setSize(stage.stageWidth, stage.stageHeight, stage.displayState); } 
   >}
   >```
   >
