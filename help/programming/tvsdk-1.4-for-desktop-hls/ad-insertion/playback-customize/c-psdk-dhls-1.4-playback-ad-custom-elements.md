---
description: TVSDK は、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。
title: 広告再生用の API 要素
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# 広告再生用の API 要素{#api-elements-for-ad-playback}

TVSDK は、広告を含むコンテンツの再生動作をカスタマイズするために使用できるクラスとメソッドを提供します。

次の API 要素は、再生をカスタマイズするのに役立ちます。

<table id="table_B07E373B9D2B425AB36466B1D42411AD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> API 要素 </th> 
   <th colname="col2" class="entry"> 広告をサポートするコンテンツ </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdvertisingMetadata</span> </td> 
   <td colname="col2">広告の時間を、閲覧者が視聴済みとしてマークするかどうか、およびマークする場合はマークするタイミングを制御します。 次を使用して監視ポリシーを設定および取得します。 
    <pre>
     の 
     <span class="codeph"> adBreakAsWatched</span> プロパティ。
    </pre> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdBreakPolicy</span> </td> 
   <td colname="col2"> 広告の時間に使用可能な再生ポリシーを列挙します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicy</span> </td> 
   <td colname="col2"> 広告に使用可能な再生ポリシーを列挙します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> AdPolicySelector</span> </td> 
   <td colname="col2"> TVSDK の広告動作をカスタマイズできるインターフェイス。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> DefaultAdPolicySelector</span> </td> 
   <td colname="col2"> デフォルトの TVSDK 動作を実装するクラス。 アプリケーションは、このクラスを上書きして、完全なインターフェイスを実装することなく、デフォルトの動作をカスタマイズできます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> MediaPlayer</span> </td> 
   <td colname="col2"> 
    <ul id="ul_37700A741403448A8760FDDA68B099AA"> 
     <li id="li_B465170D449E49489C5924572BEEB4A5"><span class="codeph"> localTime</span>. <p>これは、配置された広告の時間を除く、再生のローカル時間です。 </p> </li> 
     <li id="li_D9D68CF428904BB2B84E1BCE828A90DC"> <span class="codeph"> seekToLocal</span>. <p>ここでは、ストリーム内のローカル時間を基準にしたシークが発生します。 </p> </li> 
     <li id="li_9DBCA75537DC4824AA66B53A3FA28812"><span class="codeph"> getTimeline.convertToLocalTime</span>. <p>タイムライン上の仮想位置がローカル位置に変換されます。 </p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> TimelineItem</span> </td> 
   <td colname="col2"> 
    <ul id="ul_99AD34F823DB4F10937EE39DAD0C0B72"> 
     <li id="li_87E2DA15ECE74CFE9C9FBBE8F4B62440"><span class="codeph"> 監視</span>. <p>閲覧者が広告を視聴したかどうかを示します。 </p> </li> 
     <li id="li_A9E5A9CF701C48BC94C93F28C114778D"><span class="codeph"> localRange</span>. <p>元のコンテンツを基準とした、広告の時間または広告の開始位置と期間。 </p> </li> 
     <li id="li_070BDA0BF4184863AF44652BD5A0CCEC"><span class="codeph"> virtualRange</span>. <p>配置された広告の時間をすべて考慮した後の、仮想タイムライン上の広告の時間または広告の開始位置と期間。 </p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>
