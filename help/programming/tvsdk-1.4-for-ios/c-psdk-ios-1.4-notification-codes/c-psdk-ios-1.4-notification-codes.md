---
description: TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告、および情報通知を生成します。
seo-description: TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告、および情報通知を生成します。
seo-title: 通知コード
title: 通知コード
uuid: 8a332057-8fda-4497-9264-a2caac92e900
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# TVSDK通知システム {#tvsdk-notification-system}

TVSDK通知システムは、診断メタデータを提供する様々なエラー、警告、および情報通知を生成します。

通知オブジェクトは、プレイヤーのステータスに関する情報を提供します。 TVSDKは、時系列に並べ替えられた通知オブジェクトのリストを提供し、各通知には次のメタデータが含まれます。

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
   <td colname="2">通知タイプ。 プラットフォームに応じて、このプロパティは、 
    <ph>
      INFO、WARNまたはERROR。 これは、通知の最上位レベルのグループです。
    </ph> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> code</span></td> 
   <td colname="2">通知に割り当てられる数値表現。 
    <ul id="ul_31AB497C6FFA452496DD09B0D78687B9"> 
     <li id="li_53E75022C50246E0982E315D04EFD8B3">エラー通知イベント、100000 ～ 19999 </li> 
     <li id="li_11AE91D1325E4F718228E662C9C55F9A">警告通知イベント、200000 ～ 299999 </li> 
     <li id="li_6D3EA03845294DC2BAD1ACF507639E51">情報通知イベント、300000 ～ 399999 </li> 
    </ul> <p>エラーなどの各最上位レベルの範囲は、サブ範囲（再生エラーを表す101000 ～ 101999など）に分割されます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> name</span></td> 
   <td colname="2">SEEK_ERRORなど、コードの解読可能な説明を含む <span class="codeph"> 文字列</span>。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> メタデータ</span> </td> 
   <td colname="2">通知に関する追加の関連情報を含むキーと値のペア。 例えば、 <span class="codeph"> URL</span> という名前のキーは、エラーの原因となった無効なURLなど、通知に関連するURLの値と対になります。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> innerNotification</span></td> 
   <td colname="2">この通知に直接影響を与え <span class="codeph"> た別の</span> PTNotificationオブジェクトへの参照です。 例えば、タイムライン挿入の競合に直接対応する広告挿入の失敗に関する通知などが考えられます。 すべての通知が内部通知を提供するわけではありません。 </td> 
  </tr> 
 </tbody> 
</table>

