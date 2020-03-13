---
description: VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。
seo-description: VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。
seo-title: DVR用に拡張されたコントロールバーの作成
title: DVR用に拡張されたコントロールバーの作成
uuid: 71bfceef-baf0-40ad-a7a0-fa2e22d24e31
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# DVR用に拡張されたコントロールバーの作成 {#construct-a-control-bar-enhanced-for-dvr}

VODおよびライブストリーミングのDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間帯の概念と、クライアントのライブポイントが含まれます。

* VODの場合、シーク可能な時間の長さは、アセット全体の時間です。
* ライブストリーミングの場合、DVR（シーク可能な）時間の長さは、ライブ再生時間で開始し、クライアントのライブポイントで終了する時間範囲として定義されます。

   次の情報を記憶しておきます。

   * クライアントのライブポイントは、バッファされた長さをライブウィンドウの終端から引くことで計算されます。

      ターゲット期間は、マニフェスト内のフラグメントの最大期間以上の値です。
   * デフォルト値は10000 msです。
   * ライブ再生用のコントロールバーは、再生開始時にサムをクライアントのライブポイントに配置し、シークが許可されていない領域を示す領域を表示することで、DVRをサポートします。

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. DVR対応のコントロールバーを実装するには、シークスクラブバーを現 [在の再生位置と共に表示するの手順に従います。](../../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md) 次の点が異なります。

   * 再生範囲ではなく、シーク可能な範囲に対してのみマップされるコントロールバーを実装できます。

      シーク可能な範囲では、あらゆるユーザ操作が安全と見なされます。
   * 再生範囲に対してマップされるが、シーク可能な範囲も表示されるコントロールバーを実装できます。

      コントロールバーの場合：
   1. 再生範囲を表すオーバーレイをコントロールバーに追加します。
   1. ユーザーがシークを開始したら、を使用して、目的のシーク位置がシーク可能な範囲内にあるかどうかを確認しま `MediaPlayer.getSeekableRange`す。

      例：

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      定数を使用して、クライアントのライブポイントをシークすることもで `MediaPlayer.LIVE_POINT` きます。

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```


