---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-title: MediaResource情報にアクセスするためのMediaPlayerメソッド
title: MediaResource情報にアクセスするためのMediaPlayerメソッド
uuid: c2d18f8e-4107-42bc-a975-9b881aadd27b
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

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
   <td colname="1"> <b>ライブストリーム </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isLive():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームがライブの場合はtrue、VODの場合はfalse。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM保護</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isProtected():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームがDRM保護されている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get drmMetadataInfos():ベクトル。&lt;DRMMetadataInfo&gt;; </span> </td> 
   <td colname="3"> <p>マニフェスト内で見つかったすべてのDRMメタデータオブジェクトを一覧表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>クローズドキャプション</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean; </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックが使用可能な場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get closedCaptionsTracks():Vector.&lt;ClosedCaptionsTrack&gt;; </span> </td> 
   <td colname="3"> <p>使用可能なクローズドキャプショントラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack </span> </td> 
   <td colname="3"> <p>SelectClosedCaptionsTrackで選択された現在のクローズドキャプショントラックを取 <span class="codeph"> 得しま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack:com.adobe.mediacore.info:ClosedCaptionsTrack ) </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>代替オーディオトラック </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームに代替オーディオトラックが含まれる場合はtrue。 </p> <p>ヒント： メイン（デフォルト）のオーディオトラックも代替オーディオトラックリストの一部です。 </p> <p>TVSDK for Desktop HLSは、メインのオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、MediaPlayerItem.hasAlternateAudioがfalseを返す場合 <span class="codeph"> は、スト </span> リームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つしかない場合、このメソッドはtrueを返し、 <span class="codeph"> get AudioTracksは単一の </span> 要素（デフォルトのオーディオトラック）を持つリストを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;AudioTrack&gt;; </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;AudioTrack&gt;; </span> </td> 
   <td colname="3"> <p>使用可能な代替オーディオトラックのリストを表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedAudioTrack():AudioTrack; </span> </td> 
   <td colname="3"> <p>selectAudioTrackで選択したオーディオトラックを取 <span class="codeph"> 得しま </span>す。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack:AudioTrack ) </span> </td> 
   <td colname="3"> <p>現在のオーディオトラックにするオーディオトラックを選択します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>時間指定メタデータ</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームに時間指定メタデータが関連付けられている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get timedMetadata():Vector.&lt;TimedMetadata&gt;; </span> </td> 
   <td colname="3"> <p>ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get profiles():Vector.&lt;プロファイル&gt;; </span> </td> 
   <td colname="3"> <p>関連するビットレートプロファイルのリストを表示します。 各プロファイルのビットレートと高さと幅を取得できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>トリック再生 </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean; </span> </td> 
   <td colname="3"> <p>プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrueです。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get availablePlaybackRates():Vector.&lt;数値&gt; </span> </td> 
   <td colname="3"> <p>トリック再生機能のコンテキストで使用可能な再生速度のリストを表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアプレイヤー </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get player():MediaPlayer </span> </td> 
   <td colname="3"> <p>現在このプレーヤーに関連付けられているメディアプレイヤーを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアリソース</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource; </span> </td> 
   <td colname="3"> <p>この項目に関連付けられたメディアリソースを返します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int </span> </td> 
   <td colname="3"> <p>この項目に関連付けられたメディア識別子を返します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

