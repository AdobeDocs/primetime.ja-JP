---
description: Flash15 以降では、StageVideo を使用したハードウェアレンダリングが使用できない場合、StageVideo はソフトウェアの StageVideo オブジェクトにシームレスにフォールバックします。
title: Flash15 の StageVideo のサポート
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 0%

---

# Flash15 の StageVideo のサポート{#flash-support-for-stagevideo}

Flash15 以降では、StageVideo を使用したハードウェアレンダリングが使用できない場合、StageVideo はソフトウェアの StageVideo オブジェクトにシームレスにフォールバックします。

ソフトウェアへのFlash15 StageVideo のフォールバックに関して、次の情報を考慮します。

* アプリケーションでコードを変更する必要はありません。
* TVSDK に対する変更は不要です。

  ソフトウェアに対する StageVideo のフォールバックを使用する場合、 TVSDK を更新する必要はありません。
* アプリケーションをFlash15 用に再コンパイルする必要があります。
* Flash15 用に再コンパイルしたアプリケーションは、Flash Player15 で導入された新しい API を使用しない限り、Flash14 以前で引き続き動作します。

  Flash14 アプリケーションで新しいFlash15 API を使用する必要がある場合、実行時にFlash Player14 でアプリケーションが失敗しないように、Object 型にキャストして API を動的に呼び出す必要があります。

## HTMLオーバーレイ {#html-overlays}

Flash15 以降では、ハードウェア StageVideo が使用できなくなり、HTMLStageVideo にフォールバックした場合に、ソフトウェアオーバーレイのシームレスな表示を維持できます。 この機能を有効にするには、 `wmode=opaque`.

一部の古いブラウザーでは、ハードウェアアクセラレーションがサポートされていません。 これらの要件について詳しくは、 [StageVideo の最小要件](../../../../../tvsdk-1.4-for-desktop-hls/c-psdk-dhls-1.4-introduction/overview-prod-audience-guide/requirements/stagevideo-capabilities/r-psdk-dhls-1.4-requirements-stage-video.md). 次の場合、 `wmode=opaque`に設定すると、ビデオはソフトウェア StageVideo でレンダリングされ、パフォーマンスに影響を与える可能性があります。 通常、 `wmode=direct` ビデオを GPU に直接レンダリングするので、パフォーマンスが大幅に向上します。 ただし、このオプションはHTMLオーバーレイも上書きします。
