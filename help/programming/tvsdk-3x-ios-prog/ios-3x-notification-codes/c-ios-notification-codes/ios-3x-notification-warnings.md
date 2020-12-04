---
description: この表は、WARNタイプの通知に関する詳細情報を示しています。
seo-description: この表は、WARNタイプの通知に関する詳細情報を示しています。
seo-title: WARNING通知コード
title: WARNING通知コード
uuid: da1a561d-3b9a-468a-a24a-7b6fa62aa2e8
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 3%

---


# 警告通知コード{#warning-notification-codes}

この表は、WARNタイプの通知に関する詳細情報を示しています。

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

ほとんどの警告には、関連するメタデータ（ダウンロードに失敗したリソースのURLなど）が含まれています。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであるかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>コード</b></th> 
   <th colname="2" class="entry"><b>名前</b></th> 
   <th colname="3" class="entry"><b>内部通知&gt;/b&gt;</th> 
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
   <td colname="5"> <p>広告クリエイティブの読み込み中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201003</span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RETURNED_NO_ADS</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> INTERNAL_ERROR, AD_ID,DESCRIPTION</span> </td> 
   <td colname="5"> <p>VAST URLが無効であるか、VASTラッパーから広告が返されなかったため、広告の解決に失敗しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>背景マニフェスト</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204000  </span> </td> 
   <td colname="2"><span class="codeph"> BACKGROUND_MANIFEST_WARNING</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> BACKGROUND_MANIFEST_WARNING_</span> <span class="codeph"> ERRORBACKGROUND_MANIFEST_WARNING_</span> <span class="codeph"> NAMEDESCRIPTION</span> </td> 
   <td colname="5"> <p> バックグラウンドマニフェストのダウンロードでエラーが発生しました。 バックグラウンドマニフェストの更新に関する問題は、TVSDKの警告としてディスパッチされ、再生が停止することはありません。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 204001  </span> </td> 
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
   <td colname="1"><span class="codeph"> 210000  </span> </td> 
   <td colname="2"><span class="codeph"> UNDEFINED_TIME_RANGES  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 広告シグナリングモードは、カスタム範囲として定義されますが、範囲が定義されていません。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 210001  </span> </td> 
   <td colname="2"><span class="codeph"> INVALID_TIME_RANGES  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明  </span> </td> 
   <td colname="5"> <p> 1つ以上の時間範囲が無効で、無視または変更されます。 </p> <p> DESCRIPTIONは、無効な範囲の説明を含む文字列です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>iOS固有</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_NOT_READY  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明  </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>ADがストリームに挿入されませんでした。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270002  </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_AUDIOONLY_MISSING  </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>広告にオーディオ専用ストリームが含まれていません </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_HLS_MATCHING_BITRATE_MISSING  </span> </td> 
   <td colname="3"><span class="codeph"> AD_NOT_INSERTED  </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>コンテンツの現在のビットレートに一致する広告ストリームが見つかりません。 </p> <p>  </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270005  </span> </td> 
   <td colname="2"><span class="codeph"> AVASSET_FAILED_TO_CREATE  </span> </td> 
   <td colname="3"><span class="codeph"> PLAYBACK_ERROR  </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>AVAssetの作成時にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270006  </span> </td> 
   <td colname="2"><span class="codeph"> SITECATALYST_警告  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明  </span> </td> 
   <td colname="5"> <p>警告：sitecatalyst警告の説明を参照してください。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 270007  </span> </td> 
   <td colname="2"><span class="codeph"> NETWORK_ERROR  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> URL  </span> </td> 
   <td colname="5"> <p>ネットワークからのデータ取得中にエラーが発生しました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>adIDとソース(URL)は、`AD_ASSET`キーを持つ通知メタデータのPTAdAssetを介して取得できます。
>
>[]属性は、通知用のオプションのキーを指定します。
