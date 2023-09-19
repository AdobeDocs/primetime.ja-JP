---
description: VOD およびライブストリーミングに対する DVR のサポートを含むコントロールバーを実装できます。 DVR のサポートには、シーク可能な時間枠とクライアントのライブポイントの概念が含まれます。
title: DVR 用に拡張されたコントロールバーの作成
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# DVR 用に拡張されたコントロールバーの作成 {#construct-a-control-bar-enhanced-for-dvr}

VOD およびライブストリーミングに対する DVR のサポートを含むコントロールバーを実装できます。 DVR のサポートには、シーク可能な時間枠とクライアントのライブポイントの概念が含まれます。

* VOD の場合、シーク可能な時間の長さはアセット全体の期間です。
* ライブストリーミングの場合、DVR（シーク可能な）時間の長さは、ライブ再生時間で開始し、クライアントのライブポイントで終了する時間範囲として定義されます。

  次の情報に留意してください。

   * クライアントのライブポイントは、バッファーされた長さをライブウィンドウの終わりから引くことで計算されます。

     ターゲット期間は、マニフェスト内のフラグメントの最大期間以上の値になります。
   * デフォルト値は10000 ms です。
   * ライブ再生のコントロールバーは、再生を開始する際に最初にクライアントのライブポイントにサムを配置し、シークが許可されない領域を示す領域を表示することで、DVR をサポートします。

<!--<a id="fig_37A39A28BA714BA5A2C461357ED5BD41"></a>-->

![](assets/dvr-window.PNG){width="684"}

1. DVR をサポートするコントロールバーを実装するには、 [シークスクラブバーを現在の再生位置で表示…](../../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md) との違いは次のとおりです。

   * 再生範囲ではなく、シーク可能な範囲にのみマッピングされるコントロールバーを実装できます。

     シークに対するユーザーの操作は、シーク可能な範囲内で安全と見なすことができます。
   * 再生範囲にマッピングされ、シーク可能な範囲も表示するコントロールバーを実装できます。

     コントロールバーの場合：

   1. 再生範囲を表すオーバーレイをコントロールバーに追加します。
   1. ユーザーがシークを開始したら、目的のシーク位置がシーク可能な範囲内にあるかどうかを、 `MediaPlayer.getSeekableRange`.

      例：

      ```java
      TimeRange seekableRange = _mediaPlayer.getSeekableRange(); 
      if (seekableRange.contains(desiredSeekPosition)) { 
          _mediaPlayer.seek(desiredPosition); 
      }
      ```

      また、 `MediaPlayer.LIVE_POINT` 定数。

      ```
      mediaPlayer.seek(MediaPlayer.LIVE_POINT);
      ```
