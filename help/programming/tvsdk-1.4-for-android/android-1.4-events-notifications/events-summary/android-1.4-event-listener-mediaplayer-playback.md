---
description: TVSDKは、ビデオの再生開始など、メディアの再生操作が発生した場合に、再生イベントをディスパッチします。
seo-description: TVSDKは、ビデオの再生開始など、メディアの再生操作が発生した場合に、再生イベントをディスパッチします。
seo-title: 再生イベント
title: 再生イベント
uuid: 809a8e0e-f4d8-4013-b04a-49fb93d7ca8a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 再生イベント{#playback-events}

TVSDKは、ビデオの再生開始など、メディアの再生操作が発生した場合に、再生イベントをディスパッチします。

すべての再生関連イベントに関する通知を受け取るには、以下のイベントコールバックを含む、の `MediaPlayer.PlaybackEventListener`実装を登録する必要があります。

<table frame="all" colsep="1" rowsep="1"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> イベント </th> 
   <th colname="2" class="entry"> 意味 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="col1"><b>再生</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayComplete%28%29" format="html" scope="external"> onPlayComplete</a> </td> 
   <td colname="2"> メディアソースの終わりに達しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPlayStart%28%29" format="html" scope="external"> onPlayStart</a> </td> 
   <td colname="2"> メディアソースの再生が開始されました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> (float rate) </td> 
   <td colname="2"> ユーザーまたはTVSDKが新しい再生速度（早送り、巻き戻し、通常の速度での再生など）を選択しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlaying</a> (float rate) </td> 
   <td colname="2"> 新しい再生速度が画面に表示されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>メディア</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPrepared%28%29" format="html" scope="external"> onPrepared</a> </td> 
   <td colname="2"> メディアプレイヤーはメディアの準備に成功しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onSizeAvailable%28long,%20long%29" format="html" scope="external"> onSizeAvailable</a> (long height, long width) </td> 
   <td colname="2"> メディアのサイズが使用可能です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>メディアプレイヤー</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.PlayerState</a> state, <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> MediaPlayerNotification</a> notification) </td> 
   <td colname="2"> メディアプレイヤーの状態が変更されました。 このコールバックでは、アプリケーションがエラーを処理する必要があります。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> (long profile, long time) </td> 
   <td colname="2"> メディアプレイヤーの現在のプロファイルが変更されました。 再生中の新しいプ <span class="codeph"> ロファイルを取得するには、Profile</span> プロパティを使用します。 このイベントが <span class="codeph"> 発生した時刻を取得するには、time</span> プロパティを使用します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaplayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdated</a> </td> 
   <td colname="2">メディアプレイヤーは、次のいずれかの場合にメディアを正常に更新しました。 
    <ul> 
     <li>ライブアセットに対してマニフェストの更新が発生した場合。</li> 
     <li>VODまたはライブアセットがキャプションを閉じ、クローズドキャプショントラックに対するアクティビティが最初に見つかったとき。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>マニフェストとタイムライン</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> TimedMetadata</a> timedMetadata) </td> 
   <td colname="2"> マニフェストで新しい時間指定メタデータが見つかりました。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdated</a> </td> 
   <td colname="2">メディアプレイヤーが広告を追加または削除したので、タイムラインが更新されました。 <p>ライブアセット用に更新されたマニフェストと、古い広告の時間がタイムラインから削除されたか、新しい広告オポチュニティ（キューポイント）が見つかりました。 メディアプレイヤーは、新しい広告を解決してタイムラインに配置しようとします。 </p><p> このイベントを使用して、タイムラインに更新があるかどうかを確認します（再生中にVODが変更されない）。 その後、MediaPlayer.getTimelineを使用してタイムラインを取得 <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> できます</a>。 </p> </td> 
  </tr> 
 </tbody> 
</table>
