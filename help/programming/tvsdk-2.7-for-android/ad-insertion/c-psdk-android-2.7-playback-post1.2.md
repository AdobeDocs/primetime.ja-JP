---
description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。
seo-description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。
seo-title: 広告のデフォルトおよびカスタマイズされた再生動作
title: 広告のデフォルトおよびカスタマイズされた再生動作
uuid: 272cdfd0-799f-41e5-bf41-1620d48c992a
translation-type: tm+mt
source-git-commit: 21d1eae53cea303221de00765724e787cf6e84ef

---


# 広告のデフォルトおよびカスタマイズされた再生動作{#default-and-customized-playback-behavior-with-ads}

メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。

デフォルトの動作を上書きするには、を使用しま `AdBreakPolicySelector` す。

>[!IMPORTANT]
>
>TVSDKは、広告中のシークを無効にする方法を提供しません。 広告中のシークを無効にするようにアプリを設定することをお勧めします。

ライブ/リニアコンテンツの再生動作は次のとおりです。

* 一時停止後に再生を再開すると、一時停止時にバッファーされたコンテンツが再生されます。

   再開位置がまだ再生範囲にある場合、再生は連続している必要があります。 それ以外の場合、TVSDKは新しいライブポイントにジャンプします。 シーク操作を実行し、別の再生ポイントを選択することもできます。
* TVSDKは、アプリケーションがライブ再生に入る位置より後のキュー間で広告を解決します。

   再生は、最初のキューが解決された後に開始されます。 ライブ再生を開始する際のデフォルト値はクライアントのライブポイントですが、別の位置を選択できます。 初期位置より前のすべてのキューは、アプリケーションがDVRウィンドウでシークを実行した後に解決されます。

次の表に、TVSDKが再生中に広告と広告の時間を処理する方法を示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ビデオアクティビティ </th> 
   <th colname="col2" class="entry"> デフォルトのTVSDK動作ポリシー </th> 
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
   <td colname="col3">selectAdBreaksToPlayを使用して、スキップされた時間のうちどれを再生 <span class="codeph"> するかを選択し</span> 、AdBreak.isWatchedを使用して、既に視聴済みの時間を判 <span class="codeph"> 別します</span> 。 <p>重要： デフォルトでは、TVSDKは、広告の時間の最初の広告に入った直後に、広告の時間を視聴済みとしてマークします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1つ以上の広告の時間をスキップして、視聴済みの広告の時間まで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 広告の時間をスキップし、広告の時間の直後の位置までシークします。 </td> 
   <td colname="col3">selectPolicyForSeekIntoAdを使用して、（視聴済みステータスがtrueに設定された）広告の時間と、シークが終了した特定の広告に対して、別の広告ポリシーを指 <span class="codeph"> 定します</span>。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリがトリック再生（DVRモード）に入ります。 再生速度は、負の値（巻き戻し）または1より大きい値（早送り）に設定できます。 </td> 
   <td colname="col2"> 早送りまたは巻き戻し中にすべての広告をスキップし、トリック再生の終了後に最後にスキップした時間を再生し、再生が終了したら、ユーザーが選択したトリック再生位置までスキップします。 </td> 
   <td colname="col3">selectAdBreaksToPlayを使用して、トリック再生の終了後に、スキップされた時間のうちどれを再生するか <span class="codeph"> を選択しま</span>す。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">詳しくは、シークスクラブ <a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local"> バーを現在の再生位置で表示するを参照してください。</a> </td> 
  </tr> 
 </tbody> 
</table>