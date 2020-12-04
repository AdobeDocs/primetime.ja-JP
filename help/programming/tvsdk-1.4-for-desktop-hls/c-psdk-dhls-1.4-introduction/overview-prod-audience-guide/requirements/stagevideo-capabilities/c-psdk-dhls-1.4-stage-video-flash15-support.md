---
description: Flash15以降では、StageVideoを使用したハードウェアレンダリングを使用できない場合、StageVideoはソフトウェアStageVideoオブジェクトにシームレスにフォールバックされます。
seo-description: Flash15以降では、StageVideoを使用したハードウェアレンダリングを使用できない場合、StageVideoはソフトウェアStageVideoオブジェクトにシームレスにフォールバックされます。
seo-title: StageVideoのFlash15のサポート
title: StageVideoのFlash15のサポート
uuid: 49bd8703-016e-4fda-8773-5254d4774ec6
translation-type: tm+mt
source-git-commit: fd686391df0fa711bba99bc1bc312c9ef619f184
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Flash15のStageVideo{#flash-support-for-stagevideo}のサポート

Flash15以降では、StageVideoを使用したハードウェアレンダリングを使用できない場合、StageVideoはソフトウェアStageVideoオブジェクトにシームレスにフォールバックされます。

Flash15のStageVideoに対するフォールバックに関する次の情報を考慮してください。

* アプリケーションでコードを変更する必要はありません。
* TVSDKに対する変更は必要ありません。

   ソフトウェアに対するStageVideoフォールバックを使用する場合、TVSDKを更新する必要はありません。
* Flash15用にアプリケーションを再コンパイルする必要があります。
* Flash15用に再コンパイルしたアプリケーションは、Flash Player15で導入された新しいAPIを使用しない限り、Flash14以前で引き続き動作します。

   Flash14アプリケーションで新しいFlash15 APIを使用する必要がある場合は、実行時にFlash Player14で失敗しないように、Object型にキャストしてAPIを動的に呼び出す必要があります。

## HTMLオーバーレイ{#html-overlays}

Flash15以降では、ハードウェアStageVideoが使用できなくなり、ソフトウェアStageVideoにフォールバックした場合に、HTMLオーバーレイのシームレスな表示を維持できます。 この機能を有効にするには、`wmode=opaque`を設定します。

一部の古いブラウザーは、ハードウェアアクセラレーションをサポートしていません。 これらの要件について詳しくは、[StageVideoの最小要件](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md)を参照してください。 `wmode=opaque`を設定すると、ビデオはソフトウェアStageVideoでレンダリングされ、パフォーマンスに影響を与える可能性があります。 通常、`wmode=direct`を設定するとビデオがGPUに直接レンダリングされ、パフォーマンスが大幅に向上します。 ただし、このオプションはHTMLオーバーレイも上書きします。
