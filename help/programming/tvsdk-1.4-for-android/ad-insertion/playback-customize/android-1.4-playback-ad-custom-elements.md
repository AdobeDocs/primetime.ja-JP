---
description: TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
seo-description: TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
seo-title: 広告再生用のAPI要素
title: 広告再生用のAPI要素
uuid: 6d0ab181-9c50-431f-97bf-32e6684a7df1
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 広告再生用のAPI要素 {#api-elements-for-ad-playback}

TVSDKは、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。

次のAPI要素は、再生のカスタマイズに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API要素 </th> 
   <th colname="col2" class="entry"> 広告をサポートするコンテンツ </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdvertisingMetadata</span> </td> 
   <td colname="col2">広告の時間を、視聴者が視聴済みとしてマークするかどうか、およびマークするタイミングを制御します。 setAdBreakAsWatchedおよびgetAdBreakAsWatchedを使用して、監視ポリシーを設 <span class="codeph"> 定し</span> 、取得 <span class="codeph"> します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> 広告の時間に対して使用可能な再生ポリシーを列挙します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicy</span> </td> 
   <td colname="col2"> 広告の可能な再生ポリシーを列挙します。 </td> 
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
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> getLocalTime</span>。 <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"><span class="codeph"> seekToLocal</span>。 <p>ここでは、ストリーム内のローカル時間を基準にしてシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>タイムライン上のバーチャル位置がローカル位置に変換されます。 </p> </li> 
    </ul> <p>重要： MediaPlayerの <span class="codeph"> getLocalTime</span> は、 <span class="codeph"></span> 広告を動的に繋ぎ合わせることなく、元のコンテンツに対する現在の時間を返します。 <span class="codeph"> AdBreakのgetLocalTime</span> は <span class="codeph"></span> 、元のコンテンツを基準とした時間の開始時間を返します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreak</span> </td> 
   <td colname="col2"><span class="codeph"> isWatched</span> プロパティ。 ビューアが広告を視聴したかどうかを示します。 </td> 
  </tr> 
 </tbody> 
</table>

