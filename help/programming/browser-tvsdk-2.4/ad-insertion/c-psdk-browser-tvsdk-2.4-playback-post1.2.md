---
description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し（トリック再生モード）、広告の組み込みの影響を受けます。
title: 広告を含むデフォルトのカスタマイズされた再生動作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# 広告を含むデフォルトのカスタマイズされた再生動作{#default-and-customized-playback-behavior-with-ads}

メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し（トリック再生モード）、広告の組み込みの影響を受けます。

デフォルトの動作を上書きするには、 `AdBreakPolicySelector`.

>[!IMPORTANT]
>
>ブラウザー TVSDK は、広告中のシークを無効にする手段を提供しません。 Adobeでは、広告中のシークを無効にするようにアプリケーションを設定することをお勧めします。

次の表に、Browser TVSDK が再生中に広告および広告の時間をどのように処理するかを示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ビデオアクティビティ </th> 
   <th colname="col2" class="entry"> デフォルトのブラウザー TVSDK 動作ポリシー </th> 
   <th colname="col3" class="entry">カスタマイズは、 <span class="codeph"> AdBreakPolicySelector </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 通常の再生中に、広告の時間が発生します。 </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> ライブ/リニアの場合は、広告ブレークが既に視聴されている場合でも、広告ブレークを再生します。 </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">VOD の場合、広告の時間を再生し、広告の時間を視聴済みとしてマークします。 </li> 
    </ul> </td> 
   <td colname="col3">を使用して、広告ブレークに別のポリシーを指定します <span class="codeph"> selectPolicyForAdBreak</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をシークしてメインコンテンツに転送します。 </td> 
   <td colname="col2"> 最後にスキップされた未視聴の広告の時間を再生し、時間の再生が完了したら、目的のシーク位置で再生を再開します。 </td> 
   <td colname="col3">を使用して、再生するスキップされた休憩を選択します <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をシークしてメインコンテンツに戻ります。 </td> 
   <td colname="col2"> 広告の時間を再生せずに、目的のシーク位置までスキップします。 </td> 
   <td colname="col3">を使用して、再生するスキップされた休憩を選択します <span class="codeph"> selectAdBreaksToPlay</span>.                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間まで早送りします。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3">広告の時間と、シークが終了した特定の広告に対して、別の広告ポリシーを指定します。その際に、 <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間まで遡ります。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3">広告の時間と、シークが終了した特定の広告に対して、別の広告ポリシーを指定します。その際に、 <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、視聴済み広告の時間をスキップしてメインコンテンツまで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 最後にスキップされた広告の時間が既に視聴されている場合は、は、ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">を使用して、スキップされた時間の中で、再生するものを選択します。 <span class="codeph"> selectAdBreaksToPlay</span> を使用して、既に監視されているブレークを特定します。 <span class="codeph"> isWatched</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1 つ以上の広告の時間を早送りまたは巻き戻しし、視聴済み広告の時間にドロップします。 </td> 
   <td colname="col2"> 広告ブレークをスキップし、広告ブレークの直後の位置までシークします。 </td> 
   <td colname="col3">広告の時間（視聴済みステータスが true に設定されている）と、シークが終了する特定の広告に対して、別の広告ポリシーを指定します。その際、 <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションは、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">詳しくは、 <a href="../../browser-tvsdk-2.4/content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-seek-scrub-bar-display.md" format="dita" scope="local"> シークバーを使用する場合にシークを処理</a> </td> 
  </tr> 
 </tbody> 
</table>

## カスタム広告動作の設定 {#section_custom_ad_behaviors}

好みの動作は、の広告コンテンツファクトリで設定できます。 `retrieveAdPolicySelectorCallbackFunc` メソッド。 以下を使用すると、 `selectPolicyForAdBreak`, `selectWatchedPolicyForAdBreak`, `selectPolicyForSeekIntoAd`、および `selectAdBreaksToPlay` ポリシーを選択するメソッドをコンテンツファクトリで使用します。
