---
description: MediaPlayerItemクラスのメソッドを使用すると、読み込まれたMediaResourceが表すコンテンツストリームに関する情報を取得できます。
title: MediaResource情報にアクセスするためのMediaPlayerItemメソッド
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# MediaResource情報にアクセスするためのMediaPlayerItemメソッド{#mediaplayeritem-methods-for-accessing-mediaresource-information}

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
   <td colname="2"> <span class="codeph"> &lt;string&gt; ListgetAdTags()  </span> </td> 
   <td colname="3"> 広告配置プロセスに使用される広告タグのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>ライブストリーム</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isLive();  </span> </td> 
   <td colname="3"> ストリームがライブの場合はtrue、VODの場合はfalse。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>DRM保護</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isProtected();  </span> </td> 
   <td colname="3"> ストリームがDRM保護されている場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;drmmetadatainfo&gt; ListgetDRMMetadataInfos();  </span> </td> 
   <td colname="3"> マニフェストで見つかったすべてのDRMメタデータオブジェクトをリストします。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>クローズドキャプション</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasClosedCaptions();  </span> </td> 
   <td colname="3"> クローズドキャプショントラックが使用可能な場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;closedcaptionstrack&gt; ListgetClosedCationsTracks();  </span> </td> 
   <td colname="3"> 使用可能なクローズドキャプショントラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> ClosedCaptionsTrack get SelectedClosedCaptionsTrack();  </span> </td> 
   <td colname="3"> <span class="codeph"> SelectClosedCaptionsTrack </span>で選択された、現在のクローズドキャプショントラックを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectClosedCaptionsTrack (ClosedCaptionsTrack closedCaptionsTrack)  </span> </td> 
   <td colname="3"> クローズドキャプショントラックを現在のクローズドキャプショントラックに設定します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>代替オーディオトラック</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasAlternateAudio();  </span> </td> 
   <td colname="3"> ストリームに代替オーディオトラックがある場合はtrue。 <p>注意： メイン（デフォルト）オーディオトラックも代替オーディオトラックリストの一部です。 </p> <p>Android向けTVSDKは、メインオーディオトラックを代替オーディオトラックリストの項目の1つと見なします。 このため、<span class="codeph"> MediaPlayerItem.hasAlternateAudio </span>がfalseを返すのは、ストリームにオーディオがまったくない場合のみです。 コンテンツにオーディオトラックが1つだけある場合、このメソッドはtrueを返し、<span class="codeph"> MediaPlayerItem.getAudioTracks </span>は1つのリスト（デフォルトのオーディオトラック）を返します。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;audiotrack&gt; ListgetAudioTracks();  </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> AudioTrack getSelectedAudioTrack();  </span> </td> 
   <td colname="3"> <span class="codeph"> selectAudioTrack </span>で選択されたオーディオトラックを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectAudioTrack ( AudioTrack audioTrack )  </span> </td> 
   <td colname="3"> 現在のオーディオトラックにするオーディオトラックを選択します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>時間指定メタデータ</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean hasTimedMetadata();  </span> </td> 
   <td colname="3"> ストリームに時間指定メタデータが関連付けられている場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;timedmetadata&gt; ListgetTimedMetadata();  </span> </td> 
   <td colname="3"> ストリームに関連付けられた時間指定メタデータオブジェクトのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>複数のプロファイル（ビットレート）</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isDynamic();  </span> </td> 
   <td colname="3"> ストリームがマルチビットレート(MBR)ストリームの場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt;profile&gt; ListgetProfiles();  </span> </td> 
   <td colname="3"> 関連するビットレートプロファイルのリストを提供します。 各プロファイルのビットレート、プロファイルの高さおよび幅を取得できます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> プロファイルgetSelectedProfile()  </span> </td> 
   <td colname="3"> 現在選択されているプロファイルを取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>トリック再生</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> boolean isTrickPlaySupported();  </span> </td> 
   <td colname="3"> プレイヤーが早送り、巻き戻しおよび再開をサポートしている場合はtrue。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> &lt; Float=""&gt; ListgetAvailablePlaybackRates()  </span> </td> 
   <td colname="3"> トリック再生機能のコンテキストで使用可能な再生速度のリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> Float getSelectedPlaybackRate()  </span> </td> 
   <td colname="3"> 現在選択されている再生速度を取得します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaPlayerItemConfig getConfig()  </span> </td> 
   <td colname="3"> この項目に関連付けられた<span class="codeph"> MediaPlayerItemConfig </span>インスタンスを返します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <b>メディアリソース</b> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> MediaResource getResource();  </span> </td> 
   <td colname="3"> この項目に関連付けられているメディアリソースを返します。 </td> 
  </tr> 
  <tr rowsep="0"> 
   <td colname="2"> <span class="codeph"> int getResourceId()  </span> </td> 
   <td colname="3"> この項目に関連付けられているメディア識別子を返します。 このIDは、<span class="codeph"> MediaPlayerItemLoader.load </span>を使用して項目が読み込まれるときに設定されます。 </td> 
  </tr> 
 </tbody> 
</table>
