---
description: TVSDK 通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。
title: 通知コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 概要 {#notification-codes-overview}

TVSDK 通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。

通知オブジェクトは、プレーヤーのステータスに関連する情報を提供します。 TVSDK は、時系列に並べ替えられた通知オブジェクトのリストを提供します。 各通知には、次のメタデータが含まれます。

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 要素 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> <p>通知タイプ。 </p> <p>プラットフォームに応じて、このプロパティは列挙型で、使用可能な値は INFO、WARN、ERROR です。 これは、通知の最上位レベルのグループです。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> コード</span> </td> 
   <td colname="2"> <p>次の数値表現が通知に割り当てられます。 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">エラー通知イベント (100000 ～ 199999) </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">警告通知イベント (200000 ～ 299999) </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">情報通知イベント (300000 ～ 399999) </li> 
     </ul> </p> <p>エラーなどの各最上位範囲は、サブ範囲 ( 再生エラーを表す101000 ～ 101999など ) に分割されます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 名前</span> </td> 
   <td colname="2">人間が判読できる、通知イベントの説明（例： ）を含む文字列 <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> メタデータ</span> </td> 
   <td colname="2"> <p>通知に関する追加情報を含むキーと値のペア。 </p> <p>例えば、 <span class="codeph"> URL</span> は、エラーの原因となった無効な URL など、通知に関連する URL を示す値を提供します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>別の参照 <span class="codeph"> MediaPlayerNotification</span> この通知に直接影響を与えたオブジェクト。 </p> <p>例えば、タイムライン挿入の競合に直接対応する広告挿入の失敗に関する通知などがあります。 一部の通知に内部通知が表示されるわけではありません。 </p> </td> 
  </tr> 
 </tbody> 
</table>
