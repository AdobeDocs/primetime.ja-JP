---
description: TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
title: 広告再生用APIエレメント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---


# 広告再生用APIエレメント{#api-elements-for-ad-playback}

TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。

以下のAPIエレメントは、再生のカスタマイズに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> APIエレメント </th> 
   <th colname="col2" class="entry"> 広告をサポートするコンテンツ </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdvertisingMetadata</span> </td> 
   <td colname="col2">広告の時間を視聴者が視聴したものとしてマークするかどうかを制御します。視聴済みの場合はマークするタイミングを制御します。 <span class="codeph"> setAdBreakAsWatched</span>と<span class="codeph"> getAdBreakAsWatched</span>を使用して、監視ポリシーを設定し、取得します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> 広告の時間に使用できる再生ポリシーを列挙します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicy</span> </td> 
   <td colname="col2"> 広告に使用できる再生ポリシーを列挙します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicySelector</span> </td> 
   <td colname="col2"> TVSDKの広告動作をカスタマイズできるインターフェイス。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DefaultAdPolicySelector</span> </td> 
   <td colname="col2"> デフォルトのTVSDK動作を実装するクラス。 アプリケーションは、このクラスをオーバーライドして、完全なインターフェイスを実装せずにデフォルトの動作をカスタマイズできます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span>. <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> seekToLocal</span>。 <p>ここで、ストリーム内のローカル時間を基準にしてシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>タイムライン上のバーチャル位置がローカル位置に変換されます。 </p> </li> 
    </ul> <p>重要： <span class="codeph"> MediaPlayer</span>の<span class="codeph"> getLocalTime</span>は、動的に広告を繋ぎ合わせることなく、元のコンテンツに対する現在の時間を返します。 <span class="codeph"> getLocalTimein </span> AdBreakは、元のコンテンツに対する時間の開始時間を返し <span class="codeph"> </span> ます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatchedproperty</span> です。ビューアが広告を視聴したかどうかを示します。 </td> 
  </tr> 
 </tbody> 
</table>

