---
description: バナー広告を表示するには、バナーインスタンスを作成し、 TVSDK が広告関連のイベントをリッスンできるようにする必要があります。
title: バナー広告の表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# バナー広告の表示 {#display-banner-ads}

バナー広告を表示するには、バナーインスタンスを作成し、 TVSDK が広告関連のイベントをリッスンできるようにする必要があります。

TVSDK は、 `AdPlaybackEventListener.onAdBreakStart` イベント。

マニフェストは、次の方法でコンパニオンバナー広告を指定できます。

* HTMLスニペット
* iFrame ページの URL
* 静的画像またはAdobeFlashSWFファイルの URL

TVSDK は、各コンパニオン広告に対して、アプリケーションで使用可能なタイプを示します。

1. リスナーを `AdPlaybackEventListener.onAdBreakStart` イベントで次の処理をおこないます。

   * バナーインスタンス内の既存の広告をクリアします。
   * 次のコンパニオン広告のリストを取得します： `Ad.getCompanionAssets`.
   * コンパニオン広告のリストが空でない場合は、バナーインスタンスのリストを繰り返し処理します。

     各バナーインスタンス ( `AdAsset`) には、幅、高さ、リソースタイプ（html、iframe、静的）などの情報や、コンパニオンバナーの表示に必要なデータが含まれます。
   * ビデオ広告にコンパニオン広告が登録されていない場合、コンパニオンアセットのリストには、そのビデオ広告のデータは含まれません。
   * スタンドアロンのディスプレイ広告を表示するには、スクリプトにロジックを追加して、通常の DFP(DoubleClick for Publishers) ディスプレイ広告タグを適切なバナーインスタンスで実行します。
   * バナー情報をページ上の関数に送信し、その関数がバナーを適切な場所に表示します。

     これは通常、 `div`を検索し、関数で `div ID` バナーを表示します。
