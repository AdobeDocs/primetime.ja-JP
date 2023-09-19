---
description: MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。
title: MediaResource 情報にアクセスする MediaPlayer 属性
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# MediaResource 情報にアクセスする MediaPlayer 属性{#mediaplayer-attributes-to-access-mediaresource-information}

MediaPlayerItem クラスのメソッドを使用すると、読み込まれた MediaResource によって表されるコンテンツストリームに関する情報を取得できます。

<table frame="all" colsep="1" rowsep="1" id="table_46225307CA5B4BB1869576E0B9141E38"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 目的 </th> 
   <th colname="2" class="entry"> 属性 </th> 
   <th colname="3" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> ライブストリーム </td> 
   <td colname="2"> <span class="codeph"> live </span> </td> 
   <td colname="3"> ストリームがライブの場合は true、VOD の場合は false です。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> クローズドキャプション </td> 
   <td colname="2"> <span class="codeph"> hasClosedCaptions </span> </td> 
   <td colname="3"> クローズドキャプショントラックが使用可能な場合は true。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> closedCaptionsTracks </span> </td> 
   <td colname="3"> 使用可能なクローズドキャプショントラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedClosedCaptionsTrack </span> </td> 
   <td colname="3"> 選択されたクローズドキャプショントラックを取得します。 <span class="codeph"> selectClosedCaptionsTrack </span>. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="2"> 代替オーディオ </td> 
   <td colname="2"> <span class="codeph"> hasAlternateAudio </span> </td> 
   <td colname="3"> <p>ストリームに代替オーディオトラックがある場合は true。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> audioTracks </span> </td> 
   <td colname="3"> 使用可能な代替オーディオトラックのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> selectedAudioTrack </span> </td> 
   <td colname="3"> 
    <pre>
      で選択された、現在選択されているオーディオトラックを取得します。 
     <span class="codeph"> selectAudioTrack </span>. 
    </pre> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> 時間指定メタデータ </td> 
   <td colname="2"> <span class="codeph"> hasTimedMetadata </span> </td> 
   <td colname="3"> ストリームに時間指定メタデータが関連付けられている場合は true。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="2"> <span class="codeph"> timedMetadata </span> </td> 
   <td colname="3"> ストリームに関連付けられている時間指定メタデータオブジェクトのリストを提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1" morerows="1"> 複数のプロファイル（ビットレート） </td> 
   <td colname="2" morerows="1"> <span class="codeph"> プロファイル </span> </td> 
   <td colname="3"> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="3"> このストリームに関連付けられているビットレートプロファイルのリストを提供します。 <p>注意：各プロファイルのビットレート、およびプロファイルの高さと幅を取得できます。 </p> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"> メディアリソース </td> 
   <td colname="2"> <span class="codeph"> リソース </span> </td> 
   <td colname="3"> この項目に関連付けられているメディアリソースを返します。 </td> 
  </tr> 
 </tbody> 
</table>
