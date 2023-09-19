---
description: 広告の配置を含む、特定のメディアのタイムラインに関する情報を提供するクラスです。
title: Timeline クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Timeline クラス{#timeline-classes}

広告の配置を含む、特定のメディアのタイムラインに関する情報を提供するクラスです。

パッケージ： [com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> <p>説明 </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker </a> </span> </td> 
   <td colname="2"> TVSDK ライブラリとの統合用に設計されたコンテンツトラッキングモジュールを作成する場合に実装する必要があるプロトコルを定義するインターフェイス。 <p>このインターフェイスでは、進行状況イベントをリモートトラッキングシステムに報告する方法を定義する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> 商談 </a> </span> </td> 
   <td colname="2"> すべてのオポチュニティクラスの基本クラス。 オポチュニティクラスは、タイムライン上の「注目の対象」ポイントを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> 配置 </a> </span> </td> 
   <td colname="2"> タイムラインの配置に関連する情報をラップするクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode </a> </span> </td> 
   <td colname="2"> 配置モードの列挙（コンテンツを挿入するか置き換えるかなど）。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType </a> </span> </td> 
   <td colname="2"> タイムライン内の配置場所を示す配置タイプの列挙（例： PRE_ROLL）。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> 予約 </a> </span> </td> 
   <td colname="2"> 予約は、タイムライン上の特定の時間範囲のそれ以上の処理を制限または防止するために使用されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> タイムライン </a> </span> </td> 
   <td colname="2"> タイムラインマーカーを処理する反復子を提供するインターフェイス。 広告の時間を含む、コンテンツのタイムラインを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem </a> </span> </td> 
   <td colname="2"> クラス。 タイムライン項目の一般的な不変表現です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker </a> </span> </td> 
   <td colname="2"> タイムライン上のマーカーを表すクラス。 これは、実際のタイムライン上の関心領域を示します。 現在、関心のある地域は広告です。広告のスクラブバー UI で別の色を使用してマークしたい場合があります。 各マーカーは、位置と時間（ミリ秒単位で表現）で定義されます。 </td> 
  </tr> 
 </tbody> 
</table>
