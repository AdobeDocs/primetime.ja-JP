---
description: 広告の配置を含む、特定のメディアのタイムラインに関する情報を提供するクラスです。
seo-description: 広告の配置を含む、特定のメディアのタイムラインに関する情報を提供するクラスです。
seo-title: Timelineクラス
title: Timelineクラス
uuid: 9c06fec1-d725-4fe8-9cf5-1e3ade2b7d27
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Timelineクラス{#timeline-classes}

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
   <td colname="1"> <span class="codeph"> コンテ <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/ContentTracker.html" format="html" scope="external"> ンツトラ </a> ッカー </span> </td> 
   <td colname="2"> TVSDKライブラリとの統合を目的としたコンテンツトラッキングモジュールを作成する場合に実装する必要があるプロトコルを定義するインターフェイス。 <p>このインターフェイスでは、進行状況イベントをリモートトラッキングシステムに報告する方法を定義する必要があります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> 商 <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Opportunity.html" format="html" scope="external"> 談 </a> 数 </span> </td> 
   <td colname="2"> すべてのオポチュニティクラスの基本クラス。 オポチュニティクラスは、タイムライン上の「注目」ポイントを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> 配 <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Placement.html" format="html" scope="external"> 置 </a></span> </td> 
   <td colname="2"> タイムラインの配置に関連する情報をラップするクラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementMode.html" format="html" scope="external"> PlacementMode </a></span> </td> 
   <td colname="2"> コンテンツを挿入するか置換するかなど、配置モードの列挙。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/PlacementType.html" format="html" scope="external"> PlacementType </a></span> </td> 
   <td colname="2"> タイムライン内の配置場所を示す配置タイプの列挙；例えば、PRE_ROLLのようにします。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Reservation.html" format="html" scope="external"> 予 </a> 約 </span> </td> 
   <td colname="2"> 予約は、タイムライン上の特定の時間範囲の処理を制限または防ぐために使用されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> タイム <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/Timeline.html" format="html" scope="external"> ライ </a> ン </span> </td> 
   <td colname="2"> タイムラインマーカーを処理するイテレータを提供するインターフェイス。 広告の時間を含む、コンテンツのタイムラインを表します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> TimelineItem <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineItem.html" format="html" scope="external"></a></span> </td> 
   <td colname="2"> クラス。 タイムラインアイテムの一般的な不変表現。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> TimelineMarker <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/timeline/TimelineMarker.html" format="html" scope="external"></a></span> </td> 
   <td colname="2"> タイムライン上のマーカーを表すクラス。 これは、実際のタイムライン上の関心領域を示します。 現在、関心領域は広告で、例えば、スクラブバーUI上で別の色でマークする場合などがあります。 各マーカーは、位置と時間（それぞれミリ秒で表されます）で定義されます。 </td> 
  </tr> 
 </tbody> 
</table>

