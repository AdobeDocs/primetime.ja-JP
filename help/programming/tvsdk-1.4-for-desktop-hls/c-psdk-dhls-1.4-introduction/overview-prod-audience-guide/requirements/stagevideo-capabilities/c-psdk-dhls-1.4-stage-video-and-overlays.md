---
description: StageVideo と共にHTMLオーバーレイを使用して、UI 要素をFlash表示リストビデオプレーンに表示できます。 このプレーンは StageVideo プレーンの上にあるので、StageVideo は常にFlashの表示リスト要素の後ろに表示されます。
title: StageVideo とHTMLオーバーレイ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# StageVideo とHTMLオーバーレイ{#stagevideo-and-html-overlays}

StageVideo と共にHTMLオーバーレイを使用して、UI 要素をFlash表示リストビデオプレーンに表示できます。 このプレーンは StageVideo プレーンの上にあるので、StageVideo は常にFlashの表示リスト要素の後ろに表示されます。

HTMLオーバーレイは、ビデオのFlash表示面に表示できる UI 要素で、 `StageVideo` それ自体の面で Flash15 より前は、ハードウェアアクセラレーションが使用できない場合にHTMLオーバーレイを使用できませんでした。 Flash15 以降、HTMLオーバーレイは、次の場合に表示されます。 `StageVideo` ソフトウェアレンダリングに戻ります。

>[!IMPORTANT]
>
>システムの機能に応じて、HTMLオーバーレイを使用すると、パフォーマンスが大きく低下する場合があります。

次の情報を考慮してください。

* FLASH PLAYER15:

   * ハードウェアアクセラレーションが使用可能かどうかに関係なく、HTMLオーバーレイを使用できます。
   * HTMLオーバーレイを使用するには、 `wmode` から `opaque`.

* FLASH PLAYER14:

   * ハードウェアアクセラレーションが使用可能な場合は、 `StageVideo` 「Flash」表示リストの下にあるので、HTMLオーバーレイを使用できます。
   * ハードウェアアクセラレーションが使用できない場合、ビデオはブラウザー内の他のすべての要素の上にレンダリングされ、HTMLオーバーレイは使用できません。

次に、と共にブラウザーオーバーレイを使用する際の最小HTML要件を示します。 `StageVideo`:

* Firefox バージョン 4 以降
* Safari バージョン 4 以降
* Internet Explorer:

   * バージョン 9 以降（Windows 7 以降）
   * Windows XP のバージョン 10 以降

* Chrome バージョン 26 以降

  >[!IMPORTANT]
  >
  >Windows XP および Windows Vista での Chrome Pepper はサポートされていません。
