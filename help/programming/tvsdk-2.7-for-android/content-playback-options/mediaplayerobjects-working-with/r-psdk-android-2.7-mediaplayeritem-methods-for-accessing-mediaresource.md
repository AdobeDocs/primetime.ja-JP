---
description: MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。
title: MediaResource 情報にアクセスするための MediaPlayerItem メソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---

# MediaResource 情報にアクセスするための MediaPlayerItem メソッド {#mediaplayeritem-methods-for-accessing-mediaresource-information}

MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。

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
   <td colname="2"> <span class="codeph"> リスト&lt;string&gt; getAdTags() </span> </td> 
   <td colname="3"> 広告配置プロセスに使用される広告タグのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>ライブストリーム</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive(); </span> </td> 
   <td colname="3"> ストリームがライブの場合は true、VOD の場合は false です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM 保護</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected(); </span> </td> 
   <td colname="3"> ストリームが DRM 保護されている場合は true です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> リスト&lt;drmmetadatainfo&gt; getDRMMetadataInfos(); </span> </td> 
   <td colname="3"> マニフェストで検出されたすべての DRM メタデータオブジェクトのリストを表示します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>クローズドキャプション</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions(); </span> </td> 
   <td colname="3"> クローズドキャプショントラックが使用可能な場合は true。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> リスト&lt;closedcaptionstrack&gt; getClosedCationsTracks(); </span> </td> 
   <td colname="3"> 使用可能なクローズドキャプショントラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack(); </span> </td> 
   <td colname="3"> 現在選択されているクローズドキャプショントラックを取得します。 <span class="codeph"> SelectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack ( ClosedCaptionsTrack closedCaptionsTrack ) </span> </td> 
   <td colname="3"> クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>代替オーディオトラック</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio(); </span> </td> 
   <td colname="3"> ストリームに代替オーディオトラックがある場合は true。 <p>注意：メイン（デフォルト）のオーディオトラックも、代替オーディオトラックリストの一部です。 </p> <p>Android 向け TVSDK は、メインのオーディオトラックを、代替オーディオトラックリストの項目の 1 つと見なします。 このため、 <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> ストリームにオーディオがまったくない場合、false を返します。 コンテンツにオーディオトラックが 1 つだけある場合、このメソッドは true を返し、 <span class="codeph"> MediaPlayerItem.getAudioTracks </span> は、単一の要素（デフォルトのオーディオトラック）を持つリストを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> リスト&lt;audiotrack&gt; getAudioTracks(); </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack(); </span> </td> 
   <td colname="3"> 選択したオーディオトラックを取得します。 <span class="codeph"> selectAudioTrack </span>. </td> 
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
   <td colname="3"> ストリームに時間指定メタデータが関連付けられている場合は true。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> リスト&lt;timedmetadata&gt; getTimedMetadata(); </span> </td> 
   <td colname="3"> ストリームに関連付けられている時間指定メタデータオブジェクトのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>複数のプロファイル（ビットレート）</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic(); </span> </td> 
   <td colname="3"> ストリームがマルチビットレート (MBR) ストリームの場合は true。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> リスト&lt;profile&gt; getProfiles(); </span> </td> 
   <td colname="3"> 関連するビットレートプロファイルのリストを提供します。 各プロファイルについて、ビットレート、プロファイルの高さおよび幅を取得できます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> プロファイル getSelectedProfile() </span> </td> 
   <td colname="3"> 現在選択されているプロファイルを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>トリック再生</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported(); </span> </td> 
   <td colname="3"> True を指定すると、プレーヤーが早送り、巻き戻しおよび再開をサポートします。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> List&lt; Float&gt; getAvailablePlaybackRates() </span> </td> 
   <td colname="3"> トリック再生機能のコンテキストで使用可能な再生率のリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate() </span> </td> 
   <td colname="3"> 現在選択されている再生速度を取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig() </span> </td> 
   <td colname="3"> を返します。 <span class="codeph"> MediaPlayerItemConfig </span> この項目に関連付けられたインスタンス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>メディアリソース</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource(); </span> </td> 
   <td colname="3"> この項目に関連付けられているメディアリソースを返します。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId() </span> </td> 
   <td colname="3"> この項目に関連付けられているメディア識別子を返します。 この ID は、項目が <span class="codeph"> MediaPlayerItemLoader.load </span>. </td> 
  </tr> 
 </tbody> 
</table>
