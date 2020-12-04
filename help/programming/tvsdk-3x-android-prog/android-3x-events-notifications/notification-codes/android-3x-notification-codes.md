---
description: TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。
seo-description: TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。
seo-title: 通知コード
title: 通知コード
uuid: 6babb203-b6d4-4b11-9fae-41e7db7fd570
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# 通知コード{#notification-codes}

TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。

通知オブジェクトは、プレイヤーのステータスに関連する情報を提供します。 TVSDKは、時系列にソートされた通知オブジェクトのリストを提供します。 各通知には、次のメタデータが含まれます。

<table frame="all" colsep="1" rowsep="1" id="table_1A32EFFE1834438D8261886EC9D7250D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b> 要素</b></th> 
   <th colname="2" class="entry"><b> 説明</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span> </td> 
   <td colname="2"> <p>通知タイプ。 </p> <p>プラットフォームに応じて、このプロパティは列挙型で、INFO、WARN、ERRORの値を取り得ます。 これは、通知のトップレベルのグループです。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <span class="codeph"> code</span> </td> 
   <td colname="2"> <p>通知には、次の数値表現が割り当てられます。 
     <ul id="ul_A86BF89D6B3B410E81FAD718D3C4A9F0"> 
      <li id="li_8180972D704C40098723734DD4B45643">エラー通知イベント、100000 ～ 199999 </li> 
      <li id="li_0EC29EA5F0034E5EBFEF8E68A6498D39">警告通知イベント、200000 ～ 299999 </li> 
      <li id="li_189A53D3D7EF4960A521AB04D00DCF70">情報通知イベント、300000 ～ 399999 </li> 
     </ul> </p> <p>エラーなどのトップレベルの範囲は、それぞれサブ範囲（再生エラーを表す101000 ～ 101999など）に分けられます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR</span>など、通知イベントに関する人間が読める説明を含む文字列です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> metadata</span> </td> 
   <td colname="2"> <p>通知に関する追加の関連情報を含むキー/値のペア。 </p> <p>例えば、<span class="codeph"> URL</span>という名前のキーは、エラーの原因となった無効なURLなど、通知に関連するURLの値を提供します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span> </td> 
   <td colname="2"> <p>この通知に直接影響を与える別の<span class="codeph"> MediaPlayerNotification</span>オブジェクトへの参照です。 </p> <p>例えば、タイムライン挿入の競合に直接対応する、広告挿入の失敗に関する通知などが考えられます。 内部通知を提供しない通知もあります。 </p> </td> 
  </tr> 
 </tbody> 
</table>