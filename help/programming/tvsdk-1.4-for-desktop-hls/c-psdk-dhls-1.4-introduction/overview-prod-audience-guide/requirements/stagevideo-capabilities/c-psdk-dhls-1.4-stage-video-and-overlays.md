---
description: HTMLオーバーレイをStageVideoと共に使用して、UI要素をFlash表示リストのビデオ面に表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。
seo-description: HTMLオーバーレイをStageVideoと共に使用して、UI要素をFlash表示リストのビデオ面に表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。
seo-title: StageVideoとHTMLオーバーレイ
title: StageVideoとHTMLオーバーレイ
uuid: 84e862ab-4c35-47a2-9c4e-f792d3ef5363
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# StageVideoとHTMLオーバーレイ{#stagevideo-and-html-overlays}

HTMLオーバーレイをStageVideoと共に使用して、UI要素をFlash表示リストのビデオ面に表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。

HTMLオーバーレイは、Flash表示面に表示できるUI要素で、ビデオをその面でレンダリングす `StageVideo` る場合に使用します。 Flash 15より前は、ハードウェアアクセラレーションが使用できない場合、HTMLオーバーレイを使用できませんでした。 Flash 15以降、ソフトウェアレンダリングにフォールバックすると、HTMLオ `StageVideo` ーバーレイが表示されるようになりました。

>[!IMPORTANT]
>
>システムの機能によっては、HTMLオーバーレイを使用すると、パフォーマンスが大きくまたは小さく低下する場合があります。

次の情報を考慮してください。

* Flash Player 15の場合：

   * ハードウェアアクセラレーションが使用可能かどうかに関わらず、HTMLオーバーレイを使用できます。
   * HTMLオーバーレイを使用するには、をに設 `wmode` 定しま `opaque`す。

* Flash Player 14の場合：

   * ハードウェアアクセラレーションが使用可能 `StageVideo` な場合、はFlash表示リストの下にあるので、HTMLオーバーレイを使用できます。
   * ハードウェアアクセラレーションが使用できない場合、ビデオはブラウザー内の他のすべての要素の上にレンダリングされ、HTMLオーバーレイは使用できなくなります。

HTMLオーバーレイを使用する場合の最小ブラウザ要件は次のとおりで `StageVideo`す。

* Firefoxバージョン4以降
* Safariバージョン4以降
* Internet Explorer:

   * バージョン9以降（Windows 7以降）
   * Windows XPのバージョン10以降

* Chromeバージョン26以降

   >[!IMPORTANT]
   >
   >Windows XPおよびWindows VistaでのChrome Pepperはサポートされていません。

