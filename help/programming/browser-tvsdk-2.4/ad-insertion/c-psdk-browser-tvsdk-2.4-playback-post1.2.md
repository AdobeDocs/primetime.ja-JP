---
description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し（トリック再生モード）、広告の組み込みの影響を受けます。
seo-description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し（トリック再生モード）、広告の組み込みの影響を受けます。
seo-title: 広告のデフォルトおよびカスタマイズされた再生動作
title: 広告のデフォルトおよびカスタマイズされた再生動作
uuid: 58f11167-a764-4647-8490-05ca66eb6c47
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 広告のデフォルトおよびカスタマイズされた再生動作{#default-and-customized-playback-behavior-with-ads}

メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し（トリック再生モード）、広告の組み込みの影響を受けます。

デフォルトの動作を上書きするには、を使用しま `AdBreakPolicySelector`す。

>[!IMPORTANT]
>
>ブラウザーTVSDKは、広告中のシークを無効にする方法を提供しません。 広告中のシークを無効にするようにアプリを設定することをお勧めします。

次の表に、ブラウザーTVSDKが再生中に広告と広告の時間を処理する方法を示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ビデオアクティビティ </th> 
   <th colname="col2" class="entry"> デフォルトのブラウザーTVSDKの動作ポリシー </th> 
   <th colname="col3" class="entry">AdBreakPolicySelectorを通じて可能なカスタマイズ <span class="codeph"> 機能 </span> </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 通常の再生中に、広告の時間が発生します。 </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> ライブ/リニアの場合は、広告の時間が既に視聴済みであっても、広告の時間を再生します。 </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">VODの場合、広告の時間を再生し、広告の時間を視聴済みとしてマークします。 </li> 
    </ul> </td> 
   <td colname="col3">selectPolicyForAdBreakを使用して、広告の時間に別のポリシーを指定し <span class="codeph"> ます</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をスキップしてメインコンテンツまで早送りします。 </td> 
   <td colname="col2"> 最後にスキップされた未視聴の広告の時間を再生し、時間の再生が完了したときに、目的のシーク位置で再生を再開します。 </td> 
   <td colname="col3">selectAdBreaksToPlayを使用して、再生するスキップされた時間を <span class="codeph"> 選択します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をスキップしてメインコンテンツまで巻き戻します。 </td> 
   <td colname="col2"> 広告の時間を再生せずに、目的のシーク位置までスキップします。 </td> 
   <td colname="col3">selectAdBreaksToPlayを使用して、再生するスキップされた時間を <span class="codeph"> 選択します</span>。                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが広告の時間まで早送りします。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3">selectPolicyForSeekIntoAdを使用して、広告の時間とシークが終了した特定の広告に対して別の広告ポリシーを指定 <span class="codeph"> します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが広告の時間まで巻き戻します。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3">selectPolicyForSeekIntoAdを使用して、広告の時間とシークが終了した特定の広告に対して別の広告ポリシーを指定 <span class="codeph"> します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、視聴済みの広告の時間をスキップしてメインコンテンツまで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 最後にスキップされた広告の時間が既に視聴済みの場合は、ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">selectAdBreaksToPlayを使用して、スキップされた時間のうちどれを再生す <span class="codeph"> るかを選択し</span> 、isWatchedを使用して既に視聴済みの時間を判 <span class="codeph"> 断します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1つ以上の広告の時間をスキップして、視聴済みの広告の時間まで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 広告の時間をスキップし、広告の時間の直後の位置までシークします。 </td> 
   <td colname="col3">selectPolicyForSeekIntoAdを使用して、（視聴済みステータスがtrueに設定された）広告の時間と、シークが終了した特定の広告に対して、別の広告ポリシーを指 <span class="codeph"> 定します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">詳しくは、シークバーを使用した <a href="../../browser-tvsdk-2.4/content-playback-options-browser-tvsdk/ui-configure/t-psdk-browser-tvsdk-2.4-ui-seek-scrub-bar-display.md" format="dita" scope="local"> 場合のシークの処理を参照してください。</a> </td> 
  </tr> 
 </tbody> 
</table>

## カスタム広告動作の設定 {#section_custom_ad_behaviors}

メソッドの広告コンテンツファクトリで、好みの動作を設定で `retrieveAdPolicySelectorCallbackFunc` きます。 コンテンツファクト `selectPolicyForAdBreak`リの、、 `selectWatchedPolicyForAdBreak`お `selectPolicyForSeekIntoAd`よびメ `selectAdBreaksToPlay` ソッドを使用して、ポリシーを選択できます。
