---
description: メディア再生の動作は、シーク、一時停止、広告の組み込みの影響を受けます。
title: 広告を含むデフォルトのカスタマイズされた再生動作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# 広告を含むデフォルトのカスタマイズされた再生動作 {#default-and-customized-playback-behavior-with-ads}

メディア再生の動作は、シーク、一時停止、広告の組み込みの影響を受けます。

デフォルトの動作を上書きするには、 `PTAdPolicySelector`.

>[!IMPORTANT]
>
>VOD およびライブ/リニアストリーミングの場合、タイムラインの調整を変更することはできません。 つまり、広告が再生された後に、タイムラインから広告を削除することはできません。 ユーザーがシークバックした場合、通常のポリシーで削除する必要があった場合でも、同じ広告が再び再生されます。

>[!IMPORTANT]
>
>TVSDK は、広告中のシークを無効にする方法を提供しません。 Adobeでは、広告中のシークを無効にするようにアプリケーションを設定することをお勧めします。

次の表に、 TVSDK が再生中に広告および広告の時間をどのように処理するかを示します。

<table id="table_466538B1C2A646B89EB4F9AA111203BE"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>ビデオアクティビティ</b></th> 
   <th colname="col2" class="entry"><b>デフォルトの TVSDK 動作ポリシー</b></th> 
   <th colname="col3" class="entry"><b>PTAdPolicySelector を通じて利用可能なカスタマイズ</b></th>
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> 通常の再生中に、広告の時間が発生します。 </td> 
   <td colname="col2"></td> 
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
   <td colname="col3">を使用して、スキップされた時間の中で、再生するものを選択します。 <span class="codeph"> selectAdBreaksToPlay</span> を使用して、既に監視されているブレークを特定します。 <span class="codeph"> PTAdBreak.isWatched</span>. <p> <p>重要：デフォルトでは、 TVSDK は、広告の時間内の最初の広告を入力した直後に、広告の時間を視聴済みとしてマークします。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションが、1 つ以上の広告の時間を早送りまたは巻き戻しし、視聴済み広告の時間にドロップします。 </td> 
   <td colname="col2"> 広告ブレークをスキップし、広告ブレークの直後の位置までシークします。 </td> 
   <td colname="col3">広告の時間（視聴済みステータスが true に設定されている）と、シークが終了する特定の広告に対して、別の広告ポリシーを指定します。その際、 <span class="codeph"> selectPolicyForSeekIntoAd</span>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> アプリケーションは、カスタム広告マーカーを使用して挿入された広告をスキップして早送りします。 </td> 
   <td colname="col2"> ユーザーが選択したシーク位置までスキップします。 </td> 
   <td colname="col3"></td> 
  </tr> 
 </tbody> 
</table>
