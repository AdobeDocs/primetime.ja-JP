---
description: メディア再生の動作は、シーク、一時停止、広告の組み込みの影響を受けます。
title: 広告のデフォルトおよびカスタマイズされた再生動作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 広告{#default-and-customized-playback-behavior-with-ads}を使用したデフォルトおよびカスタマイズされた再生動作

メディア再生の動作は、シーク、一時停止、広告の組み込みの影響を受けます。

デフォルトの動作を上書きするには、`PTAdPolicySelector`を使用します。

>[!IMPORTANT]
>
>VODおよびライブ/リニアストリーミングの場合、タイムラインの調整を変更することはできません。 これは、広告の再生後に、タイムラインから広告を削除できないことを意味します。 ユーザーがシークバックすると、通常のポリシーで削除する必要があった場合でも、同じ広告が再生されます。

>[!IMPORTANT]
>
>TVSDKは、広告中のシークを無効にする手段を提供しません。 Adobeでは、広告中のシークを無効にするようにアプリを設定することをお勧めします。

次の表に、TVSDKが再生中に広告と広告の時間を処理する方法を示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>ビデオアクティビティ</b></th> 
   <th colname="col2" class="entry"><b>デフォルトのTVSDK動作ポリシー</b></th> 
   <th colname="col3" class="entry"><b>PTAdPolicySelectorを通じて可能なカスタマイズ</b></th>
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 通常の再生中に、広告の時間を検出します。 </td> 
   <td colname="col2"></td> 
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
   <td colname="col3"><span class="codeph"> selectAdBreaksToPlay</span>を使用して、スキップされた広告の時間のうちどれを再生するかを選択し、<span class="codeph"> PTAdBreak.isWatched</span>を使用して、既に視聴済みの広告の時間を判断します。 <p> <p>重要： デフォルトでは、TVSDKは、広告の時間の最初の広告に入った直後に、広告の時間を視聴済みとしてマークします。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1つ以上の広告の時間をスキップして、視聴済みの広告の時間まで早送りまたは巻き戻します。 </td> 
   <td colname="col2"> 広告の時間をスキップし、広告の時間の直後の位置までシークします。 </td> 
   <td colname="col3"><span class="codeph"> selectPolicyForSeekIntoAd</span>を使用して、広告の時間（監視ステータスがtrueに設定されている）とシークが終了した場所の特定の広告に異なる広告ポリシーを指定します。 </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>