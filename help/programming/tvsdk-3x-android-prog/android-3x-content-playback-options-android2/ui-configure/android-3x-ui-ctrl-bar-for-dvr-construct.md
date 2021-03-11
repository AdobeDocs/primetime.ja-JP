---
description: VODおよびライブストリーミング用のDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間枠の概念や、クライアントのライブポイントが含まれます。
title: DVR用に拡張されたコントロールバーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---


# DVR用に拡張されたコントロールバーの作成{#construct-a-control-bar-enhanced-for-dvr}

VODおよびライブストリーミング用のDVRサポートを備えたコントロールバーを実装できます。 DVRのサポートには、シーク可能な時間枠の概念や、クライアントのライブポイントが含まれます。

* VODの場合、シーク可能な時間の長さは、アセット全体の長さになります。
* ライブストリーミングの場合、DVR（シーク可能な）時間の長さは、ライブ再生時間に開始が到達し、クライアントのライブポイントで終了する時間範囲として定義されます。

   次の情報を覚えておいてください。

   * クライアントのライブポイントは、バッファされた長さをライブ時間の終わりから引いて計算されます。

      ターゲットの期間は、マニフェスト内のフラグメントの最大期間以上の値です。
   * デフォルト値は10000 msです。
   * ライブ再生用のコントロールバーは、再生を開始する際に、クライアントのライブポイントにサムを最初に配置し、シーク不能な領域をマークする領域を表示することで、DVRをサポートします。

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width=&quot;684&quot;}

1. DVRをサポートするコントロールバーを実装するには、[シークスクラブバーを現在の再生位置で表示するの手順に従います。](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/ui-configure/android-3x-ui-seek-scrub-bar-display.md) を次のように異なります。

   * 再生範囲ではなく、シーク可能な範囲に対してのみマップされるコントロールバーを実装できます。

      シーク可能な範囲でユーザーが操作した場合、安全と見なすことができます。
   * 再生範囲に対してマップされるが、シーク可能な範囲も表示するコントロールバーを実装できます。

      コントロールバーの場合：
   1. 再生範囲を表すコントロールバー追加へのオーバーレイ。
   1. ユーザーがシークする開始がある場合は、`MediaPlayer.getSeekableRange`を使用して、目的のシーク位置がシーク可能な範囲内にあるかどうかを確認します。

      例：

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      `MediaPlayer.LIVE_POINT`定数を使用して、クライアントライブポイントにシークすることもできます。

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
