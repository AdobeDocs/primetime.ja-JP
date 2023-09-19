---
description: 次の表に、ERROR タイプの通知の詳細を示します。
title: ERROR 通知コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 4%

---

# ERROR 通知コード{#error-notification-codes}

次の表に、ERROR タイプの通知の詳細を示します。

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

ほとんどのエラーには、関連するメタデータ（例えば、ダウンロードに失敗したリソースの URL）が含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
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
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 100000 </span> </td> 
   <td colname="2"><span class="codeph"> DRM_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> MAJOR_DRM_CODE </span><span class="codeph"> MINOR_DRM_CODE </span><span class="codeph"> 説明 </span> </td> 
   <td colname="5">106000(
     <span class="codeph"> NATIVE_ERROR</span>) をクリックします。
   </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>再生</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>フラグメントまたはセグメント（ビデオとオーディオの両方）のダウンロード中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101006 </span> </td> 
   <td colname="2"><span class="codeph"> SECURITY_ERROR </span> </td> 
   <td colname="3"> </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008</span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> <span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>一時停止操作の実行中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> <p>シーク操作の実行中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>コンテンツ期間に関する情報を取得中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>再生位置を取得しようとした際にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>QOS 情報を取得しようとした際にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> <p>データをダウンロード中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>無効なリソース </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span><span class="codeph"> リソース </span> </td> 
   <td colname="5"> <p>リソース項目の読み込み中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> <p>再生タイムラインにリソースを配置中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>広告処理 </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104000 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_FAIL </span> </td> 
   <td colname="3"><span class="codeph"> AD_METADATA _INVALID </span><span class="codeph"> AD_RESOLVER_INITIALIZATION_FAIL </span><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span><span class="codeph"> AD_RESOLVER_SERVER_UNREACHABLE </span> </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> なし </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104001 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_METADATA_INVALID </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> </td> 
   <td colname="5"> <p>広告メタデータの形式が無効なので、広告の解決に失敗しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> <p>広告プラグインが広告を解決できませんでした。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3">なし</td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> <p>広告解決フェーズが失敗しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104006 </span> </td> 
   <td colname="2"><span class="codeph"> AD_UNREACHABLE </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>ネイティブ</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106000 </span> </td> 
   <td colname="2"><span class="codeph"> NATIVE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> RUNTIME_CODE</span> <span class="codeph"> RUNTIME_CODE_MESSAGE</span> <span class="codeph"> RESOURCE_URL</span> <span class="codeph"> RESOURCE_TYPE</span> <span class="codeph"> RESOURCE_ID</span> <p><b>DRM の詳細：</b> </p> <span class="codeph"> DRM_ERROR_STRING</span> <span class="codeph"> RUNTIME_SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>低レベルの AVE ライブラリがエラーを発行しました。 </p> <p>詳しくは、 <a href="../../c-psdk-dhls-1.4-events-and-notifications/notification-codes/c-psdk-dhls-1.4-native-error-summary.md" format="html" scope="external"> NATIVE_ERROR 通知の詳細</a> を参照してください。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>AVE 低レベルライブラリのインスタンス化中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>AVE 低レベルライブラリの解放中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>AVE ライブラリで使用されている GPU リソースの解放中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>AVE ライブラリのリセット中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> <p>AVE ライブラリへのビューのアタッチ中にエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>代替オーディオ</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 109000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_ERROR </span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="4"><span class="codeph"> AUDIO_TRACK_NAME </span><span class="codeph"> AUDIO_TRACK_LANGUAGE </span> </td> 
   <td colname="5"> <p>オーディオトラックに関連するエラーが発生しました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>汎用</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 199999 </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> <p>一般的なエラーイベントを示します。 TVSDK が実際に発行したものではありません。 これは、 TVSDK エラーイベントに対応する数値コードの範囲の終わりを示すマーカーにすぎません。 </p> </td> 
  </tr> 
 </tbody> 
</table>
