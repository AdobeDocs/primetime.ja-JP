---
description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。
title: 広告を含むデフォルトのカスタマイズされた再生動作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# 広告を含むデフォルトのカスタマイズされた再生動作{#default-and-customized-playback-behavior-with-ads}

メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。

デフォルトの動作を上書きするには、 `AdBreakPolicySelector` .

>[!IMPORTANT]
>
>TVSDK は、広告中のシークを無効にする方法を提供しません。 Adobeでは、広告中のシークを無効にするようにアプリケーションを設定することをお勧めします。

ライブ/リニアコンテンツの再生動作を次に示します。

* 一時停止後に再生を再開すると、一時停止の時点でバッファーされたコンテンツが再生されます。

  再開位置が再生範囲内にある場合は、再生は連続である必要があります。 それ以外の場合、 TVSDK は新しいライブポイントにジャンプします。 シーク操作を実行し、別の再生ポイントを選択することもできます。
* TVSDK は、アプリケーションがライブ再生に入る位置より後のキュー間で広告を解決します。

  再生は、最初のキューが解決された後に開始されます。 ライブ再生を開始する際のデフォルト値はクライアントのライブポイントですが、別の位置を選択することもできます。 初期位置より前のすべてのキューは、アプリケーションが DVR ウィンドウでシークを実行した後に解決されます。

次の表に、 TVSDK が再生中に広告および広告の時間をどのように処理するかを示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ビデオアクティビティ </th> 
   <th colname="col2" class="entry"> デフォルトの TVSDK 動作ポリシー </th> 
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
   <td colname="col3">を使用して、スキップされた時間の中で、再生するものを選択します。 <span class="codeph"> selectAdBreaksToPlay</span> を使用して、既に監視されているブレークを特定します。 <span class="codeph"> AdBreak.isWatched</span> . <p>重要：デフォルトでは、 TVSDK は、広告の時間内の最初の広告を入力した直後に、広告の時間を視聴済みとしてマークします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1 つ以上の広告の時間を早送りまたは巻き戻しし、視聴済み広告の時間にドロップします。 </td> 
   <td colname="col2"> 広告ブレークをスキップし、広告ブレークの直後の位置までシークします。 </td> 
   <td colname="col3">広告の時間（視聴済みステータスが true に設定されている）と、シークが終了する特定の広告に対して、別の広告ポリシーを指定します。その際、 <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションがトリック再生（DVR モード）に入ります。 再生率は、負（巻き戻し）または 1 より大きい（早送り）に設定できます。 </td> 
   <td colname="col2"> 早送りまたは巻き戻し中にすべての広告をスキップし、トリック再生の終了後にスキップされた最後の時間を再生し、その時間で再生が終了したら、ユーザーが選択したトリック再生位置までスキップします。 </td> 
   <td colname="col3">トリック再生が終了した後に、スキップされた時間の中から、 <span class="codeph"> selectAdBreaksToPlay</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションは、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">詳しくは、 <a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local"> シークスクラブバーを現在の再生位置で表示…</a> </td> 
  </tr> 
 </tbody> 
</table>
