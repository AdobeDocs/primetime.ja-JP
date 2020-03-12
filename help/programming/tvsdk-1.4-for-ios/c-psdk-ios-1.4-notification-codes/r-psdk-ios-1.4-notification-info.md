---
description: 次の表に、INFOタイプの通知に関する詳細情報を示します。
seo-description: 次の表に、INFOタイプの通知に関する詳細情報を示します。
seo-title: INFO通知コード
title: INFO通知コード
uuid: 10145ce6-9eb0-4829-85dd-1acfe97b07e8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# INFO通知コード{#info-notification-codes}

次の表に、INFOタイプの通知に関する詳細情報を示します。

ほとんどの情報通知には、ダウンロードに失敗したリソースのURLなど、関連するメタデータが含まれます。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであったかを指定するメタデータが含まれています。

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
   <td colname="1"><span class="codeph"> 300000 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_START </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300001 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYBACK_COMPLETE </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> なし </td> 
   <td colname="5"> 再生が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300002 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_START </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> <p> なし </p> </td> 
   <td colname="5"> シーク操作が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300003 </span> </td> 
   <td colname="2"><span class="codeph"> SEEK_COMPLETE </span> </td> 
   <td colname="3"> なし </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> シーク操作が完了しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 300005 </span> </td> 
   <td colname="2"><span class="codeph"> PLAYER_STATE_CHANGE </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> プレイヤーの状態が変更されました。 状態がERRORの場合、内部通知は、スイッチをERROR状態にトリガーしたエラー通知オブジェクトです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>可変ビットレート(ABR)</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 302000 </span> </td> 
   <td colname="2"><span class="codeph"> BITRATE_CHANGE </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"><span class="codeph"> BITRATE </span> </td> 
   <td colname="5"> ビデオのビットレートが変更されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>遅延バインディングオーディオ(LBA)</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 304000 </span> </td> 
   <td colname="2"><span class="codeph"> AUDIO_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>オーディオトラックが変更されました。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>サブタイトル</b> </td> 
   <td colname="2"> </td>
   <td colname="3"> </td>
   <td colname="4"> </td>
   <td colname="5"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"> 307000 </span> </td> 
   <td colname="2"><span class="codeph"> SUBTITLES_TRACK_CHANGE </span> </td> 
   <td colname="3"> <p>なし </p> </td> 
   <td colname="4"> <p>なし </p> </td> 
   <td colname="5"> <p>サブタイトルトラックが変更されました。 </p> </td> 
  </tr> 
 </tbody> 
</table>

