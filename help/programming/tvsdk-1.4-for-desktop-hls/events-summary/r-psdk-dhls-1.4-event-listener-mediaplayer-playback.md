---
description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーの状態の変化を監視できます。
seo-description: アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーの状態の変化を監視できます。
seo-title: 再生イベント
title: 再生イベント
uuid: 6d6491d7-cf25-4130-8388-68b8c028bb71
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# 再生イベント {#playback-events}

アプリケーションは、TVSDKがディスパッチするイベントをリッスンすることで、プレイヤーのアクティビティおよびプレイヤーの状態の変化を監視できます。

TVSDKは、ビデオの再生開始など、メディアの再生操作が発生した場合に、再生イベントをディスパッチします。 すべての再生関連イベントに関する通知を受け取るには、次のイベントのリスナーをオ `MediaPlayer` ブジェクトに登録します。

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
   <td colname="2"> ユーザーまたはTVSDKが新しい再生速度（早送り、巻き戻し、通常の速度での再生など）を選択しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">PlaybackRateEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/PlaybackRateEvent.html#RATE_PLAYING" format="html" scope="external"> RATE_PLAYING</a> </td> 
   <td colname="2"> 新しい再生速度が画面に表示されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> TimeChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimeChangeEvent.html#TIME_CHANGED" format="html" scope="external"> TIME_CHANGED</a> </td> 
   <td colname="2"> メディアの現在の再生ヘッドの位置が変更されました。 現在の時間が250ミリ秒以上ごとに変更されると、定期的にディスパッチされます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>メディアプレイヤー</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerStatus ChangeEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerStatusChangeEvent.html#STATUS_CHANGED" format="html" scope="external"> STATUS_CHANGED</a> </td> 
   <td colname="2"> メディアプレイヤーのステータスが変更されました。 アプリケーションは、このイベントのコールバックでエラーを処理する必要があります。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">ProfileEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/ProfileEvent.html#PROFILE_CHANGED" format="html" scope="external"> PROFILE_CHANGED</a> </td> 
   <td colname="2">メディアプレイヤーの現在のプロファイルが変更されました。 再生中の新し <span class="codeph"> いプロファイルを取得するには</span> 、ProfileEvent.profileプロパティを使用します。 このイベントが <span class="codeph"> 発生した時刻を取得するには、time</span> プロパティを使用します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>MediaplayerItem</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItemイベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_CREATED" format="html" scope="external"> ITEM_CREATED</a> </td> 
   <td colname="2">MediaPlayerItemが作 <span class="codeph"> 成され</span> ました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1">MediaPlayerItemイベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#ITEM_UPDATED" format="html" scope="external"> ITEM_UPDATED</a> </td> 
   <td colname="2">メディアプレイヤーは、次のいずれかの場合にメディアを正常に更新しました。 
    <ul id="ul_E4D1A1D468544C3B9F8046E9B68A956D"> 
     <li id="li_35A2A417BF924E039D9CB36CFBCDFEB6">ライブアセットに対してマニフェストの更新が発生した場合。 </li> 
     <li id="li_E7AB380C212B4011B07C3B313282681C">VODまたはライブアセットがキャプションを閉じ、クローズドキャプショントラックに対するアクティビティが最初に見つかったとき。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>キャプションとオーディオ</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> MediaPlayerItemイベント。<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/MediaPlayerItemEvent.html#CAPTION_UPDATED" format="html" scope="external"> CAPTION_UPDATED</a> </td> 
   <td colname="2">メディアストリームで新しいクローズドキャプショントラックが検出され、closedCaptionsTracksコレク <span class="codeph"> ションが</span> 更新されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><b>マニフェストとタイムライン</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="0"> 
   <td colname="1">TimelineEvent.<a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/events/TimelineEvent.html#TIMELINE_UPDATED" format="html" scope="external"> TIMELINE_UPDATED</a> </td> 
   <td colname="2">メディアプレイヤーが広告を追加または削除したので、タイムラインが更新されました。 <p>ライブアセット用に更新されたマニフェストと、古い広告の時間がタイムラインから削除されたか、新しい広告オポチュニティ（キューポイント）が見つかりました。 メディアプレイヤーは、新しい広告を解決してタイムラインに配置しようとします。 </p> <p> このイベントを使用して、タイムラインに更新があるかどうかを確認します（再生中にVODが変更されない）。 その後、MediaPlayer.timelineを使用してタイムラインを取得 <a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/MediaPlayer.html#timeline" format="html" scope="external"> できます</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>

