---
description: TVSDK は、ビデオの再生開始など、メディアの再生操作が発生すると、再生イベントをディスパッチします。
title: 再生イベント
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# 再生イベント{#playback-events}

TVSDK は、ビデオの再生開始など、メディアの再生操作が発生すると、再生イベントをディスパッチします。

すべての再生関連イベントに関する通知を受け取るには、 `MediaPlayer.PlaybackEventListener`（以下のイベントコールバックを含む）

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
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRateSelected%28float%29" format="html" scope="external"> onRateSelected</a> （浮動小数点数） </td> 
   <td colname="2"> ユーザーまたは TVSDK が、通常の速度での早送り、巻き戻し、再生再開など、新しい再生レートを選択しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onRatePlaying%28float%29" format="html" scope="external"> onRatePlaying</a> （浮動小数点数） </td> 
   <td colname="2"> 新しい再生レートが画面に表示されます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>メディア</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onPrepared%28%29" format="html" scope="external"> onPrepared</a> </td> 
   <td colname="2"> メディアプレーヤーがメディアを正常に準備しました。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onSizeAvailable%28long,%20long%29" format="html" scope="external"> onSizeAvailable</a> （長い高さ、長い幅） </td> 
   <td colname="2"> メディアのサイズを使用できます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>Media Player</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onStateChanged%28com.adobe.mediacore.MediaPlayer.PlayerState,com.adobe.mediacore.MediaPlayerNotification%29" format="html" scope="external"> onStateChanged</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlayerState.html" format="html" scope="external"> MediaPlayer.PlayerState</a> 州、 <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayerNotification.html" format="html" scope="external"> MediaPlayerNotification</a> 通知 ) </td> 
   <td colname="2"> メディアプレーヤーの状態が変更されました。 アプリケーションは、このコールバックでエラーを処理する必要があります。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onProfileChanged%28long,%20long%29" format="html" scope="external"> onProfileChanged</a> （長いプロファイル、長い時間） </td> 
   <td colname="2"> メディアプレーヤーの現在のプロファイルが変更されました。 以下を使用します。 <span class="codeph"> プロファイル</span> プロパティを使用して、再生中の新しいプロファイルを取得します。 以下を使用します。 <span class="codeph"> 時間</span> プロパティを使用して、このイベントが発生した時刻を取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>MediaplayerItem</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onUpdated%28%29" format="html" scope="external"> onUpdated</a> </td> 
   <td colname="2">メディアプレーヤーは、次のいずれかの場合にメディアを正常に更新しました。 
    <ul> 
     <li>ライブアセットに対してマニフェストの更新が発生したとき。</li> 
     <li>VOD またはライブアセットがキャプションをクローズし、クローズドキャプショントラックに対するアクティビティが最初に検出されたとき。 </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="col1"><b>マニフェストとタイムライン</b></td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimedMetadata%28com.adobe.mediacore.metadata.TimedMetadata%29" format="html" scope="external"> onTimedMetadata</a> (<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/metadata/TimedMetadata.html" format="html" scope="external"> TimedMetadata</a> timedMetadata) </td> 
   <td colname="2"> マニフェストで新しい時間指定メタデータが検出されました。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.PlaybackEventListener.html#onTimelineUpdated%28%29" format="html" scope="external"> onTimelineUpdated</a> </td> 
   <td colname="2">メディアプレーヤーが広告を追加または削除したので、タイムラインが更新されました。 <p>ライブアセット用に更新されたマニフェストと、古い広告の時間がタイムラインから削除されたか、新しい広告オポチュニティ（キューポイント）が検出されました。 メディアプレーヤーは、新しい広告を解決してタイムラインに配置しようとします。 </p><p> このイベントを使用して、タイムラインに更新があるかどうかを確認します（再生中に VOD が変更されない）。 その後、 <a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/MediaPlayer.html#getTimeline%28%29" format="html" scope="external"> MediaPlayer.getTimeline</a>. </p> </td> 
  </tr> 
 </tbody> 
</table>
