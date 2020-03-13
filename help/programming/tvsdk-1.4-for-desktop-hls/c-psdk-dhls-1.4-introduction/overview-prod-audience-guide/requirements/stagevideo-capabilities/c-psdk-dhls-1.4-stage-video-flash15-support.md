---
description: Flash 15以降では、StageVideoを使用したハードウェアレンダリングが使用できない場合、StageVideoはソフトウェアのStageVideoオブジェクトにシームレスにフォールバックされます。
seo-description: Flash 15以降では、StageVideoを使用したハードウェアレンダリングが使用できない場合、StageVideoはソフトウェアのStageVideoオブジェクトにシームレスにフォールバックされます。
seo-title: Flash 15のStageVideoのサポート
title: Flash 15のStageVideoのサポート
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184

---


# Flash 15のStageVideoのサポート{#flash-support-for-stagevideo}

Flash 15以降では、StageVideoを使用したハードウェアレンダリングが使用できない場合、StageVideoはソフトウェアのStageVideoオブジェクトにシームレスにフォールバックされます。

ソフトウェアに対するFlash 15 StageVideoのフォールバックに関する次の情報を考慮してください。

* アプリケーションでコードを変更する必要はありません。
* TVSDKに対する変更は不要です。

   ソフトウェアに対するStageVideoフォールバックを使用する場合、TVSDKの更新は必要ありません。
* アプリケーションをFlash 15用に再コンパイルする必要があります。
* Flash 15用に再コンパイルしたアプリケーションは、Flash Player 15で導入された新しいAPIを使用しない限り、引き続きFlash 14以前のバージョンで動作します。

   Flash 14アプリケーションで新しいFlash 15 APIを使用する必要がある場合は、実行時にFlash Player 14で失敗しないように、Object型にキャストしてAPIを動的に呼び出す必要があります。

## HTMLオーバーレイ {#html-overlays}

Flash 15以降では、ハードウェアのStageVideoが使用できなくなり、ソフトウェアのStageVideoにフォールバックした場合に、HTMLオーバーレイのシームレスな表示を維持できます。 この機能を有効にするには、を設定しま `wmode=opaque`す。

一部の古いブラウザーは、ハードウェアアクセラレーションをサポートしていません。 これらの要件について詳しくは、StageVideoの最小要件を [参照してください](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md)。 設定すると、ビデオはソフ `wmode=opaque`トウェアのStageVideoと共にレンダリングされ、パフォーマンスに影響を与える可能性があります。 通常、を設定すると、ビデ `wmode=direct` オが直接GPUにレンダリングされ、パフォーマンスが大幅に向上します。 ただし、このオプションはHTMLオーバーレイも上書きします。
