---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
seo-title: MediaResource情報にアクセスするためのMediaPlayerメソッド
title: MediaResource情報にアクセスするためのMediaPlayerメソッド
uuid: c2d18f8e-4107-42bc-a975-9b881aadd27b
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

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
   <td colname="1"> <b>ライブストリーム  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isLive():Boolean;  </span> </td> 
   <td colname="3"> <p>ストリームがライブの場合はtrue、VODの場合はfalse。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>DRM保護</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isProtected():Boolean;  </span> </td> 
   <td colname="3"> <p>ストリームがDRM保護されている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get drmMetadataInfos():ベクトル。&lt;drmmetadatainfo&gt;;  </span> </td> 
   <td colname="3"> <p>マニフェストで見つかったすべてのDRMメタデータオブジェクトをリストします。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>クローズドキャプション</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasClosedCaptions():Boolean;  </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックが使用可能な場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get closedCaptionsTracks():Vector.&lt;closedcaptionstrack&gt;;  </span> </td> 
   <td colname="3"> <p>使用可能なクローズドキャプショントラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedClosedCaptionsTrack():ClosedCaptionsTrack  </span> </td> 
   <td colname="3"> <p><span class="codeph"> SelectClosedCaptionsTrack </span>で選択された、現在のクローズドキャプショントラックを取得します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (closedCaptionsTrack:com.adobe.mediacore.info:ClosedCaptionsTrack )  </span> </td> 
   <td colname="3"> <p>クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>代替オーディオトラック  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasAlternateAudio():Boolean;  </span> </td> 
   <td colname="3"> <p>ストリームに代替オーディオトラックがある場合はtrue。 </p> <p>ヒント： メイン（デフォルト）オーディオトラックも代替オーディオトラックリストの一部です。 </p> <p>TVSDK for Desktop HLSは、メインオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、<span class="codeph"> MediaPlayerItem.hasAlternateAudio </span>がfalseを返すのは、ストリームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つしかない場合、このメソッドはtrueを返し、<span class="codeph"> get AudioTracks </span>は1つのリスト（デフォルトのオーディオトラック）を返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get audioTracks():Vector.&lt;audiotrack&gt;;  </span> </td> 
   <td colname="3"> <p>使用可能な代替オーディオトラックのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get selectedAudioTrack():AudioTrack;  </span> </td> 
   <td colname="3"> <p><span class="codeph"> selectAudioTrack </span>で選択されたオーディオトラックを取得します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack(audioTrack:AudioTrack )  </span> </td> 
   <td colname="3"> <p>現在のオーディオトラックにするオーディオトラックを選択します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>時間指定メタデータ</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get hasTimedMetadata():Boolean;  </span> </td> 
   <td colname="3"> <p>ストリームに時間指定メタデータが関連付けられている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get timedMetadata():Vector.&lt;timedmetadata&gt;;  </span> </td> 
   <td colname="3"> <p>ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isDynamic():Boolean;  </span> </td> 
   <td colname="3"> <p>ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function getプロファイル():Vector.&lt;profile&gt;;  </span> </td> 
   <td colname="3"> <p>関連するビットレートプロファイルのリストを提供します。 各プロファイルのビットレート、プロファイルの高さおよび幅を取得できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>トリック再生  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get isTrickPlaySupported():Boolean;  </span> </td> 
   <td colname="3"> <p>プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrue。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get availablePlaybackRates():Vector.&lt;number&gt; </span> </td> 
   <td colname="3"> <p>トリック再生機能のコンテキストで使用可能な再生速度のリストを提供します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアプレイヤ  </b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get player():MediaPlayer  </span> </td> 
   <td colname="3"> <p>現在このプレイヤーに関連付けられているメディアプレイヤーを返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> <b>メディアリソース</b> </td> 
   <td colname="2"> </td>
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> function get resource():MediaResource;  </span> </td> 
   <td colname="3"> <p>この項目に関連付けられているメディアリソースを返します。 </p> </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> function get resourceId():int  </span> </td> 
   <td colname="3"> <p>この項目に関連付けられているメディア識別子を返します。 </p> </td> 
  </tr> 
 </tbody> 
</table>

