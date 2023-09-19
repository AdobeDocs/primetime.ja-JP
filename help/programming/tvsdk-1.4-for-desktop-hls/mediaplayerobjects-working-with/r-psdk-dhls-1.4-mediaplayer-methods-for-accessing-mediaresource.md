---
description: MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。
title: MediaResource 情報にアクセスするための MediaPlayer メソッド
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MediaResource 情報にアクセスするための MediaPlayer メソッド{#mediaplayer-methods-for-accessing-mediaresource-information}

MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。

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
   <td colname="3"> <p>ストリームがライブの場合は true、VOD の場合は false です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM 保護</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isProtected():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームが DRM 保護されている場合は true です。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get drmMetadataInfos(): Vector.&lt;drmmetadatainfo&gt;; </span> </td> 
   <td colname="3"> <p>マニフェストで検出されたすべての DRM メタデータオブジェクトのリストを表示します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>クローズドキャプション</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean; </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックが使用可能な場合は true。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get closedCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;; </span> </td> 
   <td colname="3"> <p>使用可能なクローズドキャプショントラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack </span> </td> 
   <td colname="3"> <p>現在選択されているクローズドキャプショントラックを取得します。 <span class="codeph"> SelectClosedCaptionsTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack: com.adobe.mediacore.info:ClosedCaptionsTrack ) </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>代替オーディオトラック </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームに代替オーディオトラックがある場合は true。 </p> <p>ヒント：メイン（デフォルト）のオーディオトラックも、代替オーディオトラックリストの一部です。 </p> <p>Desktop HLS 向け TVSDK は、メインのオーディオトラックを、代替オーディオトラックリストの項目の 1 つと見なします。 このため、 <span class="codeph"> MediaPlayerItem.hasAlternateAudio </span> ストリームにオーディオがまったくない場合、false を返します。 コンテンツにオーディオトラックが 1 つだけある場合、このメソッドは true を返し、 <span class="codeph"> AudioTracks を取得 </span> は、単一の要素（デフォルトのオーディオトラック）を持つリストを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;; </span> </td> 
   <td colname="3"> <p>使用可能な代替オーディオトラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedAudioTrack():AudioTrack; </span> </td> 
   <td colname="3"> <p>選択したオーディオトラックを取得します。 <span class="codeph"> selectAudioTrack </span>. </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack: AudioTrack ) </span> </td> 
   <td colname="3"> <p>現在のオーディオトラックにするオーディオトラックを選択します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>時間指定メタデータ</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームに時間指定メタデータが関連付けられている場合は true。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get timedMetadata():Vector.&lt;timedmetadata&gt;; </span> </td> 
   <td colname="3"> <p>ストリームに関連付けられている時間指定メタデータオブジェクトのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean; </span> </td> 
   <td colname="3"> <p>ストリームがマルチビットレート (MBR) ストリームの場合は true。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get profiles():Vector.&lt;profile&gt;; </span> </td> 
   <td colname="3"> <p>関連するビットレートプロファイルのリストを提供します。 各プロファイルについて、ビットレート、プロファイルの高さおよび幅を取得できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>トリック再生 </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean; </span> </td> 
   <td colname="3"> <p>True を指定すると、プレーヤーが早送り、巻き戻しおよび再開をサポートします。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get availablePlaybackRates():Vector.&lt;Number&gt; </span> </td> 
   <td colname="3"> <p>トリック再生機能のコンテキストで使用可能な再生率のリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアプレーヤー </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get player():MediaPlayer </span> </td> 
   <td colname="3"> <p>このプレーヤーに現在関連付けられているメディアプレーヤーを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアリソース</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource; </span> </td> 
   <td colname="3"> <p>この項目に関連付けられているメディアリソースを返します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int </span> </td> 
   <td colname="3"> <p>この項目に関連付けられているメディア識別子を返します。 </p> </td> 
  </tr> 
 </tbody> 
</table>
