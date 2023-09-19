---
description: この表は、WARN タイプの通知に関する詳細な情報を示します。
title: 警告通知コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# 警告通知コード {#warning-notification-codes}

この表は、WARN タイプの通知に関する詳細な情報を示します。

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

ほとんどの警告には、ダウンロードに失敗したリソースの URL など、関連するメタデータが含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>コード</b></th> 
   <th colname="2" class="entry"><b>名前</b></th> 
   <th colname="3" class="entry"><b>内部通知 &gt;/b&gt;</th> 
   <th colname="4" class="entry"><b>メタデータキー</b></th> 
   <th colname="5" class="entry"><b>コメント</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>広告解決</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201002</span> </td> 
   <td colname="2"><span class="codeph"> AD_ASSET_FAILED_TO_LOAD</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> AD_ASSET, INTERNAL_ERROR</span> </td> 
   <td colname="5"> <p>広告クリエイティブを読み込もうとした際にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201003</span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RETURNED_NO_ADS</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID,DESCRIPTION</span> </td> 
   <td colname="5"> <p>VAST URL が無効なため、または VAST ラッパーから広告が返されなかったため、広告の解決に失敗しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>背景マニフェスト</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000 </span> </td> 
   <td colname="2"><span class="codeph"> BACKGROUND_MANIFEST_WARNING</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> BACKGROUND_MANIFEST_WARNING_ERROR</span> <span class="codeph"> BACKGROUND_MANIFEST_WARNING_NAME</span> <span class="codeph"> 説明</span> </td> 
   <td colname="5"> <p> バックグラウンドマニフェストのダウンロード中にエラーが発生しました。 バックグラウンドマニフェストの更新時に発生した問題は、TVSDK 警告としてディスパッチされ、再生が停止することはありません。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_SEEK_WARNING</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> <p></p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>TimeRangeCollection</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210000 </span> </td> 
   <td colname="2"><span class="codeph"> UNDEFINED_TIME_RANGES </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 広告シグナリングモードは、カスタム範囲として定義されますが、定義された範囲はありません。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210001 </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_TIME_RANGES </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p> 1 つ以上の時間範囲が無効で、無視または変更されます。 </p> <p> DESCRIPTION は、無効な範囲の説明を含む文字列です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>iOS固有</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_NOT_READY </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>AD がストリームに挿入されませんでした。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270002 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_AUDIOONLY_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>広告にオーディオ専用ストリームが含まれていません </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_MATCHING_BITRATE_MISSING </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>コンテンツの現在のビットレートに一致する広告ストリームが見つかりません。 </p> <p>  </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270005 </span> </td> 
   <td colname="2"><span class="codeph"> AVASSET_FAILED_TO_CREATE </span> </td> 
   <td colname="3"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>AVAsset の作成中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270006 </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_警告 </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>警告： sitecatalyst の警告の説明を参照してください。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270007 </span> </td> 
   <td colname="2"><span class="codeph"> NETWORK_ERROR </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>ネットワークからデータを取得中にエラーが発生しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adID とソース (URL) は、PTAdAsset を通じて、 `AD_ASSET` キー。
>
>The [] 属性は、通知用のオプションのキーを指定します。
