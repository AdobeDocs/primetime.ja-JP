---
description: メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。
title: 広告のデフォルトおよびカスタマイズされた再生動作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# ads{#default-and-customized-playback-behavior-with-ads}によるデフォルトおよびカスタマイズされた再生動作

メディア再生の動作は、シーク、一時停止、早送りまたは巻き戻し、広告の影響を受けます。

デフォルトの動作を上書きするには、`AdBreakPolicySelector`を使用します。

>[!IMPORTANT]
>
>TVSDKは、広告中のシークを無効にする手段を提供しません。 Adobeでは、広告中のシークを無効にするようにアプリを設定することをお勧めします。

ライブ/リニアコンテンツの再生動作は次のとおりです。

* 一時停止後に再生を再開すると、一時停止の時点でバッファーされたコンテンツの再生が行われます。

   再開位置がまだ再生範囲にある場合、再生は連続している必要があります。 それ以外の場合は、TVSDKは新しいライブポイントにジャンプします。 シーク操作を実行し、別の再生ポイントを選択することもできます。
* TVSDKは、アプリケーションがライブ再生に入る位置より後のキュー間で広告を解決します。

   再生は、最初のキューが解決された後に開始されます。 ライブ再生に入るデフォルト値はクライアントのライブポイントですが、別の位置を選択できます。 初期位置より前のすべてのキューは、アプリケーションがDVRウィンドウでシークを実行した後に解決されます。

次の表に、TVSDKが再生中に広告と広告の時間を処理する方法を示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ビデオアクティビティ </th> 
   <th colname="col2" class="entry"> デフォルトのTVSDK動作ポリシー </th> 
   <th colname="col3" class="entry"><span class="codeph"> AdBreakPolicySelector </span>を通じて可能なカスタマイズ </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 通常の再生中に、広告の時間を検出します。 </td> 
   <td colname="col2"> 
    <ul id="ul_10D2638676EA4ADDA718E61BD4FDC1D2"> 
     <li id="li_D5CC30F063934C738971E2E8AF00C137"> ライブ/リニアの場合は、広告の時間が既に視聴済みであっても、広告の時間を再生します。 </li> 
     <li id="li_D962C0938DA74186AE99D117E5A74E38">VODの場合、広告の時間を再生し、広告の時間を視聴済みとしてマークします。 </li> 
    </ul> </td> 
   <td colname="col3"><span class="codeph"> selectPolicyForAdBreak</span>を使用して、広告の時間に別のポリシーを指定します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をスキップしてメインコンテンツまで早送りします。 </td> 
   <td colname="col2"> 最後にスキップされた未視聴の広告の時間を再生し、広告の時間の再生が完了したら、目的のシーク位置で再生を再開します。 </td> 
   <td colname="col3"><span class="codeph"> selectAdBreaksToPlay</span>を使用して、スキップした広告の時間を選択して再生します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間をスキップしてメインコンテンツまで巻き戻します。 </td> 
   <td colname="col2"> 広告の時間を再生せずに、目的のシーク位置までスキップします。 </td> 
   <td colname="col3"><span class="codeph"> selectAdBreaksToPlay</span>を使用して、スキップした広告の時間を選択して再生します。                      </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間まで早送りします。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3"><span class="codeph"> selectPolicyForSeekIntoAd</span>を使用して、広告の時間とシークが終了した場所の特定の広告に異なる広告ポリシーを指定します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、広告の時間まで巻き戻します。 </td> 
   <td colname="col2"> シークが終了した広告の先頭から再生します。 </td> 
   <td colname="col3"><span class="codeph"> selectPolicyForSeekIntoAd</span>を使用して、広告の時間とシークが終了した特定の広告に異なる広告ポリシーを指定します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、視聴済みの広告の時間をスキップしてメインコンテンツまで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 最後にスキップされた広告の時間が既に視聴済みの場合は、ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3"><span class="codeph"> selectAdBreaksToPlay</span>を使用して、スキップされた広告の時間のうちどれを再生するかを選択し、<span class="codeph"> AdBreak.isWatched</span>を使用して、既に視聴済みの広告の時間を判断します。 <p>重要： デフォルトでは、TVSDKは、広告の時間の最初の広告に入った直後に、広告の時間を視聴済みとしてマークします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1つ以上の広告の時間をスキップして、視聴済みの広告の時間まで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 広告の時間をスキップし、広告の時間の直後の位置までシークします。 </td> 
   <td colname="col3"><span class="codeph"> selectPolicyForSeekIntoAd</span>を使用して、広告の時間（監視ステータスがtrueに設定されている）とシークが終了した場所の特定の広告に異なる広告ポリシーを指定します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションがトリック再生（DVRモード）に入ります。 再生速度は、負の値（巻き戻し）または1より大きい値（早送り）にできます。 </td> 
   <td colname="col2"> 早送りまたは巻き戻し中はすべての広告をスキップし、トリック再生終了後に、最後にスキップされた広告の時間を再生し、その時間の再生が終了したら、ユーザーが選択したトリック再生位置までスキップします。 </td> 
   <td colname="col3"><span class="codeph"> selectAdBreaksToPlay</span>を使用して、トリック再生終了後にスキップされた広告の時間のうちどれを再生するかを選択します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3">詳しくは、<a href="../../tvsdk-2.7-for-android/content-playback-options/ui-configure/t-psdk-android-2.7-ui-seek-scrub-bar-display.md" format="dita" scope="local">シークスクラブバーを現在の再生位置で表示するを参照してください。</a> </td> 
  </tr> 
 </tbody> 
</table>