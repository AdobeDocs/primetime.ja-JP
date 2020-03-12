---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-title: MediaResource情報にアクセスするためのMediaPlayerItemメソッド
title: MediaResource情報にアクセスするためのMediaPlayerItemメソッド
uuid: c6e77eb7-cefd-48aa-9373-2b44a96217a5
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# MediaResource情報にアクセスするためのMediaPlayerItemメソッド {#mediaplayeritem-methods-for-accessing-mediaresource-information}

MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。

<table frame="all" colsep="1" rowsep="1" id="table_F6006A9167044AC087A6ECB20B8CCD5D"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> メソッド </th> 
   <th colname="3" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="2"> <b>広告タグ</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;String&gt; getAdTags() </span> </td> 
   <td colname="3"> 広告配置プロセスに使用される広告タグのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>ライブストリーム</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> ストリームがライブの場合はtrue、VODの場合はfalse。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM保護</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> ストリームがDRM保護されている場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;DRMMetadataInfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> マニフェスト内で見つかったすべてのDRMメタデータオブジェクトを一覧表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>クローズドキャプション</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> クローズドキャプショントラックが使用可能な場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;ClosedCaptionsTrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> 使用可能なクローズドキャプショントラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> SelectClosedCaptionsTrackで選択された現在のクローズドキャプショントラックを取 <span class="codeph"> 得しま </span>す。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>代替オーディオトラック</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> ストリームに代替オーディオトラックが含まれる場合はtrue。 <p>注意： メイン（デフォルト）のオーディオトラックも代替オーディオトラックリストの一部です。 </p> <p>Android向けTVSDKは、メインのオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、MediaPlayerItem.hasAlternateAudioがfalseを返す場合 <span class="codeph"> は、スト </span> リームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つしかない場合、このメソッドはtrueを返し、 <span class="codeph"> MediaPlayerItem.getAudioTracksは単一の </span> 要素（デフォルトのオーディオトラック）を持つリストを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> selectAudioTrackで選択したオーディオトラックを取 <span class="codeph"> 得しま </span>す。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> 現在のオーディオトラックにするオーディオトラックを選択します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>時間指定メタデータ</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata(); </span> </td> 
   <td colname="3"> ストリームに時間指定メタデータが関連付けられている場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;TimedMetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>複数のプロファイル（ビットレート）</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;Profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> 関連するビットレートプロファイルのリストを表示します。 各プロファイルのビットレートと高さと幅を取得できます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Profile getSelectedProfile() </span> </td> 
   <td colname="3"> 現在選択されているプロファイルを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>トリック再生</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported(); </span> </td> 
   <td colname="3"> プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrueです。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt; Float&gt; getAvailablePlaybackRates() </span> </td> 
   <td colname="3"> トリック再生機能のコンテキストで使用可能な再生速度のリストを表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate() </span> </td> 
   <td colname="3"> 現在選択されている再生レートを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig() </span> </td> 
   <td colname="3"> この項目に関連付 <span class="codeph"> けられ </span> たMediaPlayerItemConfigインスタンスを返します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>メディアリソース</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> この項目に関連付けられたメディアリソースを返します。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId() </span> </td> 
   <td colname="3"> この項目に関連付けられたメディア識別子を返します。 このIDは、アイテムがMediaPlayerItemLoader.loadを使用して読み込まれると <span class="codeph"> きに設定されま </span>す。 </td> 
  </tr> 
 </tbody> 
</table>
