---
description: この表は、WARNタイプの通知に関する詳細情報を示しています。
seo-description: この表は、WARNタイプの通知に関する詳細情報を示しています。
seo-title: WARNING通知コード
title: WARNING通知コード
uuid: 32b54e6c-f107-4e8e-aad6-34e1057719b0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 2%

---


# 警告通知コード{#warning-notification-codes}

この表は、WARNタイプの通知に関する詳細情報を示しています。

<!--<a id="section_F25366B6703040E3ADA993C113618F01"></a>-->

ほとんどの警告には、関連するメタデータ（ダウンロードに失敗したリソースのURLなど）が含まれています。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであるかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_C24772DF203B4DB2ACE6B475698C4C58"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> コード </th> 
   <th colname="2" class="entry"> 名前 </th> 
   <th colname="3" class="entry"> 内部通知 </th> 
   <th colname="4" class="entry"> メタデータキー </th> 
   <th colname="5" class="entry"> コメント </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>再生</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 200000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_OPERATION _FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AUDIO_TRACK_ERROR  </span><span class="codeph"> SEEK_ERROR  </span> </td> 
   <td colname="4"><span class="codeph"> 説明  </span> </td> 
   <td colname="5"> <p>再生関連の操作に失敗しましたが、再生は継続する場合があります。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>広告解決</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 201000  </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL  </span> </td> 
   <td colname="3"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL  </span><span class="codeph"> RESOURCE_PLACEMENT_FAILED  </span><span class="codeph"> AD_RESOLVER_METADATA_INVALID  </span> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>広告リゾルバーが広告コンテンツの解決/挿入に失敗しました。 再生は継続する場合があります。 </p> </td> 
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
   <td colname="5"> <p> </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>ネイティブ</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"><span class="codeph"> 209100  </span> </td> 
   <td colname="2" morerows="1"><span class="codeph"> NATIVE_WARNING  </span> </td> 
   <td colname="3" morerows="1"> <p>なし </p> </td> 
   <td colname="4"><b>AVE</b> <p><span class="codeph"> NATIVE_ERROR_CODE  </span><span class="codeph"> NATIVE_ERROR_NAME  </span><span class="codeph"> DESCRIPTION  </span> </p> </td> 
   <td colname="5"> <p>低レベルAVEライブラリがエラーを発行しました。 </p> <p>これらのメタデータフィールドの値について詳しくは、<a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> NATIVE_ERROR通知</a>の詳細を参照してください。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="4"><b>DRM</b> <p><span class="codeph"> NATIVE_SUBERROR_</span> <span class="codeph"> CODEDRM_ERROR_STRING</span> </p> </td> 
   <td colname="5"> DRMマイナーエラーコードとDRMサーバーエラー文字列。 これらのメタデータフィールドの値について詳しくは、<a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> NATIVE_ERROR通知</a>の詳細を参照してください。</td> 
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
   <td colname="1"><b>トリックモード</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 280000  </span> </td> 
   <td colname="2"><span class="codeph"> TRICKPLAY_RATE_CHANGE_FAIL</span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> <p> レート変更に失敗しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>汎用</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 299999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_WARNING  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>一般的な警告イベントを示します。 TVSDKによって実際に発行されるわけではありません。 これは、警告イベントに対応する数値コードの範囲の終わりを示すマーカーに過ぎません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[注意！] adIDとソース(URL)は、 `AD_ASSET` キーを持つ通知メタデータのPTAdAssetを介して取得できます。
