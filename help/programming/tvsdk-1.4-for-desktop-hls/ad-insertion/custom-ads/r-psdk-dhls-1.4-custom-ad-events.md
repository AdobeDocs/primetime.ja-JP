---
description: TVSDKプレイヤーは、イベントをディスパッチして、カスタム広告の読み込みステータスを表示したり、読み込みに時間がかかりすぎたりエラーが発生した広告を無視したりします。 これらのイベントは、イベント.CustomAdEventsで定義されます。
seo-description: TVSDKプレイヤーは、イベントをディスパッチして、カスタム広告の読み込みステータスを表示したり、読み込みに時間がかかりすぎたりエラーが発生した広告を無視したりします。 これらのイベントは、イベント.CustomAdEventsで定義されます。
seo-title: カスタム広告イベント
title: カスタム広告イベント
uuid: 78e2ccf4-5943-4c60-84be-623182d9a300
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# カスタム広告イベント{#custom-ad-events}

TVSDKプレイヤーは、イベントをディスパッチして、カスタム広告の読み込みステータスを表示したり、読み込みに時間がかかりすぎたりエラーが発生した広告を無視したりします。 これらのイベントは、イベント.CustomAdEventsで定義されます。

<table id="table_718700E0F0B042F882ED131F79E01D4E"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> イベント </th> 
   <th colname="col2" class="entry"> 定義 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdClickThru  </span> </td> 
   <td colname="col2"> ビューアがカスタム広告をクリックした回数。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdError  </span> </td> 
   <td colname="col2"> カスタム広告でエラーが発生しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoaded  </span> </td> 
   <td colname="col2"> カスタム広告が読み込まれました。  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdLoading  </span> </td> 
   <td colname="col2"> カスタム広告を読み込んでいます。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPaused  </span> </td> 
   <td colname="col2"> カスタム広告が一時停止しました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdResumed  </span> </td> 
   <td colname="col2"> カスタム広告は一時停止後も再生を続けました。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdPlaying  </span> </td> 
   <td colname="col2"> カスタム広告を再生中です。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> AdProgress  </span> </td> 
   <td colname="col2"> <p>カスタム広告プレイヤーは、カスタム広告の進行状況をTVSDKプレイヤーに通知します。 &amp;nbsp; </p> <p>広告の<span class="codeph"> currentTime </span>と<span class="codeph"> totalTime </span>がこのイベントに渡されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStarted </td> 
   <td colname="col2"> カスタム広告の再生が開始され、ビューアに表示されます。  </td> 
  </tr> 
  <tr> 
   <td colname="col1"> AdStopped </td> 
   <td colname="col2"> カスタム広告の再生が終了しました。 </td> 
  </tr> 
 </tbody> 
</table>

<!--<a id="section_027774C2A47C453BA9DED61C6F8567C3"></a>-->

