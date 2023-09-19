---
description: TVSDK がディスパッチするイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーの状態の変化をアプリケーションで監視できます。
title: 再生イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# 再生イベント {#playback-events}

TVSDK がディスパッチするイベントをリッスンすることで、プレーヤーのアクティビティとプレーヤーの状態の変化をアプリケーションで監視できます。

TVSDK は、ビデオの再生開始など、メディアの再生操作が発生すると、再生イベントをディスパッチします。 すべての再生関連イベントに関する通知を受け取るには、 `MediaPlayer` オブジェクトを次のイベントに設定します。

<table frame="all" colsep="1" rowsep="1" id="table_922EEA3DE0BD47BA982E11F890CA0A6B"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> イベント </th> 
   <th colname="2" class="entry"> 意味 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><b>再生</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_SELECTED" format="html" scope="external"> RATE_SELECTED</a> </td> 
   <td colname="2"> ユーザーまたは TVSDK が、通常の速度での早送り、巻き戻し、再生再開など、新しい再生レートを選択しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> 新しい再生レートが画面に表示されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> メディアの現在の再生ヘッドの位置が変更されました。 現在の時刻が 250 ms 以上ごとに変更されると、定期的にディスパッチされます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>Media Player</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> メディアプレーヤーのステータスが変更されました。 アプリケーションは、このイベントのコールバックでエラーを処理する必要があります。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> PROFILE_CHANGED</a> </td> 
   <td colname="2">メディアプレーヤーの現在のプロファイルが変更されました。 以下を使用します。 <span class="codeph"> ProfileEvent.profile</span> プロパティを使用して、再生中の新しいプロファイルを取得します。 以下を使用します。 <span class="codeph"> 時間</span> プロパティを使用して、このイベントが発生した時刻を取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaplayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem イベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">A <span class="codeph"> MediaPlayerItem</span> が作成されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItem イベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_UPDATED</a> </td> 
   <td colname="2">メディアプレーヤーは、次のいずれかの場合にメディアを正常に更新しました。 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">ライブアセットに対してマニフェストの更新が発生したとき。 </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">VOD またはライブアセットがキャプションをクローズし、クローズドキャプショントラックに対するアクティビティが最初に検出されたとき。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>キャプションとオーディオ</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItem イベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">新しいクローズドキャプショントラックがメディアストリームおよび <span class="codeph"> closedCaptionsTracks</span> コレクションが更新されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>マニフェストとタイムライン</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">メディアプレーヤーが広告を追加または削除したので、タイムラインが更新されました。 <p>ライブアセット用に更新されたマニフェストと、古い広告の時間がタイムラインから削除されたか、新しい広告オポチュニティ（キューポイント）が検出されました。 メディアプレーヤーは、新しい広告を解決してタイムラインに配置しようとします。 </p> <p> このイベントを使用して、タイムラインに更新があるかどうかを確認します（再生中に VOD が変更されない）。 その後、 <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> MediaPlayer.timeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
