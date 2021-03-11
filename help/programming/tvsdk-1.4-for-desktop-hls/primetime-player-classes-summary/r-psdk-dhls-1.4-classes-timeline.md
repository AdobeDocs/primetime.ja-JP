---
description: 広告の配置など、特定のメディアのタイムラインに関する情報を提供するクラスです。
title: Timelineクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Timeline classes{#timeline-classes}

広告の配置など、特定のメディアのタイムラインに関する情報を提供するクラスです。

パッケージ：[com.adobe.mediacore.timeline](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_6752E908BA6546549619994A3F7D5F87"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> <p>説明 </p> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ContentTracker  </a> </span> </td> 
   <td colname="2"> TVSDKライブラリと統合するコンテンツトラッキングモジュールを作成する場合に実装する必要があるプロトコルを定義するインターフェイス。 <p>このインターフェイスでは、進行状況イベントをリモートトラッキングシステムに報告する方法を定義する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> オポチュニティ  </a> </span> </td> 
   <td colname="2"> すべてのオポチュニティクラスのベースクラス。 オポチュニティクラスは、タイムライン上の「注目」点を表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> 配置  </a> </span> </td> 
   <td colname="2"> タイムラインの配置に関連する情報をラップするクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode  </a> </span> </td> 
   <td colname="2"> コンテンツを挿入するか置換するかなど、配置モードの定義済みリスト。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType  </a> </span> </td> 
   <td colname="2"> タイムライン内の配置場所を示す配置タイプの定義済みリスト。例えば、PRE_ROLLです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> 予約  </a> </span> </td> 
   <td colname="2"> 予約は、タイムライン上の特定の時間範囲の処理を制限または防止するために使用します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> タイムライン  </a> </span> </td> 
   <td colname="2"> タイムラインマーカーを処理する反復子を提供するインターフェイス。 広告の時間を含む、コンテンツのタイムラインを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"> TimelineItem  </a> </span> </td> 
   <td colname="2"> クラス。 タイムライン項目の一般的な不変表現。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"> TimelineMarker  </a> </span> </td> 
   <td colname="2"> タイムライン上のマーカーを表すクラス。 実際のタイムライン上の目標領域を示します。 現在、関心のある領域は広告です。例えば、広告をスクラブバーUIで別の色でマークする場合などがあります。 各マーカーは、位置と時間で定義されます（それぞれがミリ秒で表されます）。 </td> 
  </tr> 
 </tbody> 
</table>

