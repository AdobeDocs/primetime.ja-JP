---
description: VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。
seo-description: VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。
seo-title: DVR用に拡張されたコントロールバーの作成
title: DVR用に拡張されたコントロールバーの作成
uuid: 08f943e8-90da-4860-92dd-dd289fd68cba
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# DVR用に拡張されたコントロールバーの作成{#construct-a-control-bar-enhanced-for-dvr}

VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。

* VODの場合、シーク可能な時間の長さは、アセット全体の時間です。
* ライブストリーミングの場合、DVR（シーク可能な）時間の長さは、ライブ再生時間で開始し、クライアントのライブポイントで終了する時間範囲として定義されます。

   クライアントのライブポイントは、バッファされた長さをライブウィンドウの終端から引くことで計算されます。 ターゲット期間は、マニフェスト内のフラグメントの最大期間以上の値です。

   デフォルト値は10000 msです。

   ライブ再生用のコントロールバーは、再生開始時にサムをクライアントのライブポイントに配置し、シークが許可されていない領域を示す領域を表示することで、DVRをサポートします。

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. DVRをサポートするコントロールバーを実装するには、シークスクラブバーを表示する手順に従い、若干の違いがあります。

   * 再生範囲ではなく、シーク可能な範囲に対してのみマップされるコントロールバーを実装できます。 シーク可能な範囲では、あらゆるユーザ操作が安全と見なされます。
   * 再生範囲に対してマップされるが、シーク可能な範囲も表示されるコントロールバーを実装するように選択できます。

      コントロールバーの場合：
   1. 再生範囲を表すオーバーレイをコントロールバーに追加します。
   1. ユーザーがシークを開始したら、プロパティを使用して、目的のシーク位置がシーク可能な範囲内にあるかどうかを確認 `MediaPlayer.seekableRange` します。

      例：

      ```
      var desiredPosition:Number = // TODO : choose a value 
      
      private function onStatusChange(event:MediaPlayerStatusChangeEvent):void { 
          switch(event.status) { 
              case MediaPlayerStatus.PREPARED: 
                  _mediaPlayer.prepareToPlay(desiredPosition); 
          } 
      }
      ```

      定数を使用して、クライアントのライブポイントをシークすることもで `MediaPlayer.LIVE_POINT` きます。

      ```
      private function onSeekToLiveClick(event:MouseEvent):void { 
          _player.seek(DefaultMediaPlayer.LIVE_POINT); 
      }
      ```


