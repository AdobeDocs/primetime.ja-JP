---
description: 次の表に、INFOタイプの通知に関する詳細情報を示します。
title: INFO通知コード
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 4%

---


# INFO通知コード{#info-notification-codes}

次の表に、INFOタイプの通知に関する詳細情報を示します。

## セクションタイトル{#section_ED4302E363AE48CBA2C3E0B71AE612D8}

ほとんどの情報通知には、ダウンロードに失敗したリソースのURLなど、関連するメタデータが含まれています。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであるかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
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
   <td colname="1"><span class="codeph"> 300000  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_開始  </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE  </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 再生が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_開始  </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> シーク操作が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003  </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE  </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"><span class="codeph"> SEEK_TIME</span> </td> 
   <td colname="5"> シーク操作が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300004  </span> </td> 
   <td colname="2"><span class="codeph"> CONTENT_CHANGE  </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> <span class="codeph"> CONTENT_</span> <span class="codeph"> IDCURRENT_MEDIA_TIME</span> </td> 
   <td colname="5"> 現在の再生時間が、メインコンテンツと代替コンテンツの境界を超えました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005  </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE  </span> </td> 
   <td colname="3"> <p>任意のERROR通知。 </p> </td> 
   <td colname="4"><span class="codeph"> STATE  </span> </td> 
   <td colname="5"> プレイヤーの状態が変更されました。 状態がERRORの場合、内部通知は、スイッチをERROR状態にトリガーしたエラー通知オブジェクトです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300100  </span> </td> 
   <td colname="2"><span class="codeph"> LOAD_INFO_AVAILABLE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> FRAGMENT_</span> <span class="codeph"> URLFRAGMENT_</span> <span class="codeph"> SIZEFRAGMENT_DOWNLOAD_</span> <span class="codeph"> DURATIONPERIOD_INDEX</span> </td> 
   <td colname="5"> ビデオセグメントのダウンロード方法に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300101  </span> </td> 
   <td colname="2"><span class="codeph"> VIDEO_SIZE_CHANGED  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> HEIGHT</span> <p><span class="codeph"> 幅</span> </p> </td> 
   <td colname="5"> ビデオ再生ウィンドウのサイズが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>可変ビットレート(ABR)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 302000  </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> BITRATE  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> ビデオのビットレートが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>広告処理  </b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303000  </span> </td> 
   <td colname="2"><span class="codeph"> TIMELINE_CHANGE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> CONTENT_ID  </span><span class="codeph"> PERIOD_INDEX  </span> </td> 
   <td colname="5"> タイムラインが変更されました（例えば、代替コンテンツが追加または削除されました）。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303001  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_ PLACEMENT_COMPLETE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> PROPOSED_AD_</span> <span class="codeph"> BREAKACCEPTED_AD_BREAK</span> </td> 
   <td colname="5"> 提案された広告の時間がTVSDKによって受け入れられ、（その全体または一部が）再生タイムラインに配置されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303002  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_開始  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> 特定の広告の時間の再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303003  </span> </td> 
   <td colname="2"><span class="codeph"> AD_BREAK_COMPLETE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> AD_BREAK  </span> </td> 
   <td colname="5"> 特定の広告の時間の再生が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303004  </span> </td> 
   <td colname="2"><span class="codeph"> AD_開始  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> 特定の広告の再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303005  </span> </td> 
   <td colname="2"><span class="codeph"> AD_COMPLETE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> </td> 
   <td colname="5"> 特定の広告の再生が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 303006  </span> </td> 
   <td colname="2"><span class="codeph"> AD_PROGRESS  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <span class="codeph"> AD_BREAK</span> <p><span class="codeph"> AD</span> </p> <span class="codeph"> PROGRESS</span> </td> 
   <td colname="5"> 特定の広告の再生が、その特定の広告の特定の割合に達しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>遅延バインディングオーディオ(LBA)</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000  </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> TRACK_ID  </span><span class="codeph"> CURRENT_MEDIA_TIME  </span> </td> 
   <td colname="5"> <p>オーディオトラックが変更されました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>DRM</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 305000  </span> </td> 
   <td colname="2"><span class="codeph"> DRM_METADATA_AVAILABLE  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> PREFETCH_TIMESTAMP  </span> </td> 
   <td colname="5"> <p>新しいDRMデータが使用可能です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>汎用</b> </td> 
   <td colname="2"> </td> 
   <td colname="3"> </td> 
   <td colname="4"> </td> 
   <td colname="5"> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><span class="codeph"> 399999  </span> </td> 
   <td colname="2"><span class="codeph"> GENERIC_INFO  </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>汎用イベントを示します。 TVSDKによって実際に発行されるわけではありません。 これは、TVSDK情報イベントに対応する数値コードの範囲の終わりを示すマーカーに過ぎません。 </p> </td> 
  </tr> 
 </tbody> 
</table>

