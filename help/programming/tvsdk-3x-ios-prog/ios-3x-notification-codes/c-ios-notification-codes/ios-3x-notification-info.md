---
description: この表は、INFO タイプの通知に関する詳細情報を示しています。
title: INFO 通知コード
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 4%

---

# INFO 通知コード {#info-notification-codes}

この表は、INFO タイプの通知に関する詳細情報を示しています。

ほとんどの情報通知には、関連するメタデータ（例えば、ダウンロードに失敗したリソースの URL）が含まれます。 一部の通知には、メインのビデオコンテンツ、代替のオーディオコンテンツ、広告のどちらで問題が発生したかを指定するメタデータが含まれています。

<table frame="all" colsep="1" rowsep="1" id="table_503463046E764A87B10EB5D8B294EB23"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>コード</b></th> 
   <th colname="2" class="entry"><b>名前</b></th> 
   <th colname="3" class="entry"><b>内部通知</b></th> 
   <th colname="4" class="entry"><b>メタデータキー</b></th> 
   <th colname="5" class="entry"><b>コメント</b></th> 
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
   <td colname="5"> プレーヤーの状態が変更されました。 状態が ERROR の場合、内部通知は、スイッチを ERROR 状態にトリガーしたエラー通知オブジェクトです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>可変ビットレート (ABR)</b> </td> 
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
   <td colname="1"><b>遅延バインディングオーディオ (LBA)</b> </td> 
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
   <td colname="1"><b>字幕</b> </td> 
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
   <td colname="5"> <p>サブタイトルのトラックが変更されました。 </p> </td> 
  </tr> 
 </tbody> 
</table>
