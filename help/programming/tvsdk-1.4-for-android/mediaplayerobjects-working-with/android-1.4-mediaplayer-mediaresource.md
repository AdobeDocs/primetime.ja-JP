---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-title: MediaResource情報にアクセスするためのMediaPlayerメソッド
title: MediaResource情報にアクセスするためのMediaPlayerメソッド
uuid: 5d83491c-6577-46fe-98af-83f0fde7a7d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaResource情報にアクセスするためのMediaPlayerメソッド{#mediaplayer-methods-for-accessing-mediaresource-information}

MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。

<table frame="all" colsep="1" rowsep="1" id="table_77B55D506FE24326A03D97AA087231FF"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="2" class="entry"> メソッド </th> 
   <th colname="3" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <b>広告タグ</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;String&gt; getAdTags() </span> </td> 
   <td colname="3"> <p>広告配置プロセスに使用される広告タグのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>ライブストリーム</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> <p>ストリームがライブの場合はtrue、VODの場合はfalse。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM保護</b> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> <p>ストリームがDRM保護されている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;DRMMetadataInfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> <p>マニフェスト内で見つかったすべてのDRMメタデータオブジェクトを一覧表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>クローズドキャプション</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックが使用可能な場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;ClosedCaptionsTrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> <p>使用可能なクローズドキャプショントラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> <p>SelectClosedCaptionsTrackで選択された現在のクローズドキャプショントラックを取 <span class="codeph"> 得しま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack) </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>代替オーディオトラック</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> <p>ストリームに代替オーディオトラックが含まれる場合はtrue。 </p> <p>ヒント： メイン（デフォルト）のオーディオトラックも代替オーディオトラックリストの一部です。 </p> <p>Android向けTVSDKは、メインのオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、MediaPlayerItem.hasAlternateAudioがfalseを返す場合 <span class="codeph"> は、スト </span> リームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つしかない場合、このメソッドはtrueを返し、 <span class="codeph"> MediaPlayerItem.getAudioTracksは単一の </span> 要素（デフォルトのオーディオトラック）を持つリストを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;AudioTrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> <p>使用可能な代替オーディオトラックのリストを表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> <p>selectAudioTrackで選択したオーディオトラックを取 <span class="codeph"> 得しま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack ) </span> </td> 
   <td colname="3"> <p>現在のオーディオトラックにするオーディオトラックを選択します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>時間指定メタデータ</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata(); </span> </td> 
   <td colname="3"> <p>ストリームに時間指定メタデータが関連付けられている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;TimedMetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> <p>ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> <p>ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt;Profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> <p>関連するビットレートプロファイルのリストを表示します。 各プロファイルのビットレートと高さと幅を取得できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>トリック再生</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported(); </span> </td> 
   <td colname="3"> <p>プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrueです。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt; Float&gt; getAvailablePlaybackRates </span> </td> 
   <td colname="3"> <p>トリック再生機能のコンテキストで使用可能な再生速度のリストを表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアリソース</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> <p>この項目に関連付けられたメディアリソースを返します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

