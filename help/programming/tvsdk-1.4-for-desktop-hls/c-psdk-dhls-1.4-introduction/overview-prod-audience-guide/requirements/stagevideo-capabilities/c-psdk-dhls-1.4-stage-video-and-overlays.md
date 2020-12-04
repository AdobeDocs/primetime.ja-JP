---
description: HTMLオーバーレイとStageVideoを使用して、Flash表示リストのビデオ面にUI要素を表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。
seo-description: HTMLオーバーレイとStageVideoを使用して、Flash表示リストのビデオ面にUI要素を表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。
seo-title: StageVideoとHTMLオーバーレイ
title: StageVideoとHTMLオーバーレイ
uuid: 84e862ab-4c35-47a2-9c4e-f792d3ef5363
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# StageVideoとHTMLオーバーレイ{#stagevideo-and-html-overlays}

HTMLオーバーレイとStageVideoを使用して、Flash表示リストのビデオ面にUI要素を表示できます。 この平面はStageVideo平面の上にあるので、StageVideoは常にFlash表示リスト要素の背後に表示されます。

HTMLオーバーレイは、`StageVideo`によって独自の平面にレンダリングされるビデオのFlash表示面に表示できるUI要素です。 Flash15より前のバージョンでは、ハードウェアアクセラレーションが使用できない場合にHTMLオーバーレイを使用できませんでした。 Flash15以降、`StageVideo`がソフトウェアレンダリングにフォールバックすると、HTMLオーバーレイが表示されます。

>[!IMPORTANT]
>
>HTMLオーバーレイを使用すると、システムの機能に応じて、パフォーマンスが大または小さく低下する場合があります。

次の情報を考慮してください。

* Flash Player15:

   * ハードウェアアクセラレーションが使用可能かどうかに関係なく、HTMLオーバーレイを使用できます。
   * HTMLオーバーレイを使用するには、`wmode`を`opaque`に設定します。

* Flash Player14:

   * ハードウェアアクセラレーションが使用可能な場合、`StageVideo`はFlash表示リストの下にあるので、HTMLオーバーレイを使用できます。
   * ハードウェアアクセラレーションが使用できない場合、ビデオはブラウザー内の他のすべての要素の上にレンダリングされるので、HTMLオーバーレイは使用できません。

以下に、`StageVideo`と共にHTMLオーバーレイを使用する場合の最小ブラウザ要件を示します。

* Firefoxバージョン4以降
* Safariバージョン4以降
* Internet Explorer:

   * Windows 7以降のバージョン9以降
   * Windows XPでのバージョン10以降

* Chromeバージョン26以降

   >[!IMPORTANT]
   >
   >Windows XPおよびWindows VistaでのChrome Pepperはサポートされていません。

