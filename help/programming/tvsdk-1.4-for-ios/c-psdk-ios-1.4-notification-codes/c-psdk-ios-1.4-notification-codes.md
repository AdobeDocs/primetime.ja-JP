---
description: TVSDK 通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。
title: 通知コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# TVSDK 通知システム {#tvsdk-notification-system}

TVSDK 通知システムは、診断メタデータを提供する様々なエラー、警告および情報通知を生成します。

通知オブジェクトは、プレーヤーのステータスに関する情報を提供します。 TVSDK は、時系列に並べ替えられた通知オブジェクトのリストを提供し、各通知には次のメタデータが含まれます。

<table frame="all" colsep="1" rowsep="1" id="table_DBA8CACF02DB4AF2B053E560850B49CE"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 要素 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> type</span></td> 
   <td colname="2">通知タイプ。 プラットフォームに応じて、このプロパティは、次の値を指定できる列挙型を参照します。 
    <pre>
      情報、警告またはエラー。 これは、通知の最上位レベルのグループです。
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> コード</span></td> 
   <td colname="2">通知に割り当てられた数値表現。 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">エラー通知イベント (100000 ～ 199999) </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">警告通知イベント (200000 ～ 299999) </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">情報通知イベント (300000 ～ 399999) </li> 
    </ul> <p>エラーなどの各最上位範囲は、サブ範囲 ( 再生エラーを表す101000 ～ 101999など ) に分割されます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 名前</span></td> 
   <td colname="2">人間が判読できるコードの説明（例： ）を含む文字列 <span class="codeph"> SEEK_ERROR</span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> メタデータ</span> </td> 
   <td colname="2">通知に関する追加情報を含むキーと値のペア。 例えば、 <span class="codeph"> URL</span> は通知に関連する URL である値（エラーの原因となった無効な URL など）と対になります。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span></td> 
   <td colname="2">別の参照 <span class="codeph"> PTNotification</span> この通知に直接影響を与えたオブジェクト。 例えば、タイムライン挿入の競合に直接対応する広告挿入の失敗に関する通知などがあります。 一部の通知に内部通知が表示されるわけではありません。 </td> 
  </tr> 
 </tbody> 
</table>
