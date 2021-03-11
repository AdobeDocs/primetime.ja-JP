---
description: TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。
title: 通知コード
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---


# 概要{#notification-codes-overview}

TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。

通知オブジェクトは、プレイヤーのステータスに関する情報を提供します。 TVSDKは、時系列にソートされた通知オブジェクトのリストを提供し、各通知には次のメタデータが含まれます。

<table frame="all" colsep="1" rowsep="1" id="table_DBA8CACF02DB4AF2B053E560850B49CE"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 要素 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> type </td> 
   <td colname="2"> 通知タイプ。 プラットフォームに応じて、このプロパティは列挙型を参照し、可能な値はINFO、WARN、またはERRORです。 これは、通知のトップレベルのグループです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> code </td> 
   <td colname="2">通知に割り当てられる数値表現： 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">エラー通知イベント、100000 ～ 199999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">警告通知イベント、200000 ～ 299999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">情報通知イベント、300000 ～ 399999 </li> 
    </ul> <p>エラーなどのトップレベルの範囲は、それぞれサブ範囲（再生エラーを表す101000 ～ 101999など）に分けられます。 </p>
    <pre>
     定義済みリスト 
     <span class="codeph"> mediacore.PSDKErrorCode</span>は、可能な値をリストします。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> name </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR</span>など、コードに関する人間が読める説明を含む文字列です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> metadata </td> 
   <td colname="2">通知に関する追加の関連情報を含むキー/値のペア。 例えば、<span class="codeph"> URL</span>という名前のキーは、エラーの原因となった無効なURLなど、通知に関連するURLの値と対になります。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"> innerNotification </td> 
   <td colname="2">この通知に直接影響を与えた別の<span class="codeph"> MediaPlayerNotification</span>オブジェクトへの参照です。 例えば、タイムライン挿入の競合に直接対応する、広告挿入の失敗に関する通知などが考えられます。 内部通知を提供しない通知もあります。 </td> 
  </tr> 
 </tbody> 
</table>

