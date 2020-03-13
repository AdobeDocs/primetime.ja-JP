---
description: 次の表に、ERRORタイプ通知の詳細を示します。
seo-description: 次の表に、ERRORタイプ通知の詳細を示します。
seo-title: ERROR通知コード
title: ERROR通知コード
uuid: cc21473d-924e-475d-96ea-352233f664ef
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# ERROR通知コード{#error-notification-codes}

次の表に、ERRORタイプ通知の詳細を示します。

<!--<a id="section_D29404228F5E4B818642CBA6A0D39546"></a>-->

ほとんどのエラーには、ダウンロードに失敗したリソースのURLなど、関連するメタデータが含まれます。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであったかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_8B61210A406A45ACBE37FC29729DDE22"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> コード </th> 
   <th colname="2" class="entry"> 名前 </th> 
   <th colname="3" class="entry"> InnerNotification </th> 
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
   <td colname="1"><span class="codeph"> 101000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101004 </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_ERROR</span> </td> 
   <td colname="3"><span class="codeph"> DOWNLOAD_ERROR</span> </td> 
   <td colname="4"> </td> 
   <td colname="5"> フラグメントまたはセグメント（ビデオとオーディオの両方）のダウンロード中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101008 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span><span class="codeph"> DESIRED_SEEK_POSITION </span><span class="codeph"> DESIRED_SEEK_PERIOD </span> </td> 
   <td colname="5"> シーク操作の実行中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101009 </span> </td> 
   <td colname="2"><span class="codeph"> PAUSE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> 一時停止操作の実行中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101102 </span> </td> 
   <td colname="2"><span class="codeph"> PERIOD_INFO_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> コンテンツ期間に関する情報の取得中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101103 </span> </td> 
   <td colname="2"><span class="codeph"> RETRIEVE_TIME_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> 再生位置の取得中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101104 </span> </td> 
   <td colname="2"><span class="codeph"> GET_QOS_DATA_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> QOS情報を取得しようとしてエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 101200 </span> </td> 
   <td colname="2"><span class="codeph"> DOWNLOAD_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> URL </span> </td> 
   <td colname="5"> データのダウンロード中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>無効なリソース</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102100 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_LOAD_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明リソ </span><span class="codeph"> ース </span> </td> 
   <td colname="5"> リソース項目の読み込み中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 102101 </span> </td> 
   <td colname="2"><span class="codeph"> RESOURCE_PLACEMENT_FAILED </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID </span> </td> 
   <td colname="5"> 再生タイムラインにリソースを配置中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>広告処理</b> </td> 
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
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> 広告メタデータの形式が無効なため、広告の解決に失敗しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104003 </span> </td> 
   <td colname="2"><span class="codeph"> AD_RESOLVER_RESOLVE_FAIL </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> NATIVE_ERROR_CODE </span> </td> 
   <td colname="5"> 広告プラグインが広告を解決できませんでした。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 104005 </span> </td> 
   <td colname="2"><span class="codeph"> AD_INSERTION_FAIL </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> PROPOSED_AD_BREAK</span> </td> 
   <td colname="5"> 広告解決フェーズが失敗しました。 </td> 
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
   <td colname="4"> <span class="codeph"> NATIVE_ERROR_CODE </span> NATIVE_ERROR_NAME <span class="codeph"> DESCRIPTION </span><span class="codeph"></span><span class="codeph"> DESCRIPTION</span> <p><b>DRMの詳細：</b> </p> <span class="codeph"> DRM_ERROR_STRING</span> NATIVE <span class="codeph"> _SUBERROR_CODE</span> </td> 
   <td colname="5"> <p>低レベルAVEライブラリがエラーを発行しました。 </p> <p>これら <a href="../../../tvsdk-1.4-for-android/android-1.4-tvsdk-notification/notification-codes/native-error-summary/android-1.4-native-error-summary.md" format="html" scope="external"> のメタデータキーの値について詳しくは</a> 、NATIVE_ERROR通知の詳細を参照してください。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106001 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_CREATION_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> AVE低レベルライブラリのインスタンス化中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106002 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RELEASE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> AVE低レベルライブラリの解放中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106003 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESOURCES_RELEASE_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> AVEライブラリで使用されるGPUリソースの解放中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106004 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_RESET_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> AVEライブラリのリセット中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 106005 </span> </td> 
   <td colname="2"><span class="codeph"> ENGINE_SET_VIEW_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> AVEライブラリへのビューのアタッチ中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>設定</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107000 </span> </td> 
   <td colname="2"><span class="codeph"> SET_VOLUME_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION VOLUME </span> </td> 
   <td colname="5"> ボリュームレベルの設定中にエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107001 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_TIME_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> バッファリングパラメーターを変更しようとしてエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107002 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_VISIBILITY_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> CCトラックの表示/非表示を変更しようとしてエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107003 </span> </td> 
   <td colname="2"><span class="codeph"> SET_CC_STYLING_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明</span> </td> 
   <td colname="5"> CCトラックのスタイル設定オプションを変更しようとしてエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107004 </span> </td> 
   <td colname="2"><span class="codeph"> SET_ABR_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> 説明 </span> </td> 
   <td colname="5"> ABR制御パラメーターを変更しようとしてエラーが発生しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 107005 </span> </td> 
   <td colname="2"><span class="codeph"> SET_BUFFER_PARAMETERS_ERROR </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> DESCRIPTION </span><span class="codeph"> INITIAL_BUFFER_TIME </span><span class="codeph"> PLAY_BUFFER_TIME </span> </td> 
   <td colname="5"> バッファリング制御パラメーターを変更しようとしてエラーが発生しました。 </td> 
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
   <td colname="5"> オーディオトラックに関連するエラーが発生しました。 </td> 
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
   <td colname="2"><span class="codeph"> GENERIC_ERROR</span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 一般的なエラーイベントを示します。 TVSDKによって実際に発行されるわけではありません。 これは、TVSDKエラーイベントに対応する数値コードの範囲の終わりのマーカーのみです。 </td> 
  </tr> 
 </tbody> 
</table>

