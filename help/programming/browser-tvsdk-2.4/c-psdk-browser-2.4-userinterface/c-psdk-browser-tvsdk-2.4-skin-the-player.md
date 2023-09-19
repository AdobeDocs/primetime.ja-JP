---
description: 以下の情報は、プレーヤーのスキン設定に役立ちます。 ビジュアル構成ごとに、対応する動作がデフォルトの動作で指定されます。
title: プレーヤーのスキニング
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---

# プレーヤーのスキニング {#skinning-the-player}

以下の情報は、プレーヤーのスキン設定に役立ちます。 ビジュアル構成ごとに、対応する動作がデフォルトの動作で指定されます。

>[!IMPORTANT]
>
>このドキュメントのスキニングの詳細は、UI フレームワークで作成されるデフォルトの UI 要素に関するものです。 プレーヤーでこれらの要素を変更した場合は、スキニング要素も変更する必要があります。

## コンテナ div {#section_99B0D598219D4150B57E97D5381B118F}

コンテナ div のスタイルは次のとおりです。

>[!TIP]
>
>これらの div は、 `common-styles.css` ファイル。

メイン div のスタイルは次のとおりです。

<table id="table_AC5745DF725543ADBBCD68BA6130DF12"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>メイン Div</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-main-video-div-style</span> </td> 
   <td colname="col2"> <p>ビデオを再生するメイン div のスタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-mode-active</span> </td> 
   <td colname="col2"> <p>PIP モードがアクティブな場合に使用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> videoBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>ピクチャーインピクチャー (PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>PIP ビデオを再生する div のスタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .view-as-main-video</span> </td> 
   <td colname="col2"> <p>スワップされ、メインビデオとして表示されるときに、初期 PIP に適用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>マルチビデオ視聴</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-view-container</span> </td> 
   <td colname="col2"> <p>マルチビデオ表示で使用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-view-view</span> </td> 
   <td colname="col2"> <p>マルチビュー内の各ビデオに配置される共通の CSS スタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>マルチビュー内の各ビデオを格納するコンテナがマルチビュー内にある場合。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 各種コントロール {#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

一般的なプレーヤーコントロールのスタイルを次に示します。

>[!TIP]
>
>これらのスタイルは、 `default-controls.css` ファイル。

<table id="table_0ACB6BAB5DAD42DBBD18CA7C0385A261"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control</span> </td> 
   <td colname="col2"> <p>スクラバーとスペースを除く、コントロールバーのすべてのコントロールに適用可能 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-slider</span> </td> 
   <td colname="col2"> <p>入力スライダー </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>パネルのヘッダー </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical-list-menu-item</span> </td> 
   <td colname="col2"> <p>縦書きのメニューリスト </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-spacer</span> </td> 
   <td colname="col2"> <p>コントロールバーのスペース </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>区切り記号（横） </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-title</span> </td> 
   <td colname="col2"> <p>パネルのタイトル </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-close-btn</span> </td> 
   <td colname="col2"> <p>パネルを閉じるためのボタン </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-button-background</span> </td> 
   <td colname="col2"> <p>すべてのボタンの背景 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-txt-control</span> </td> 
   <td colname="col2"> <p>テキストコントロールのデフォルトのスタイル。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## コントロールバー {#section_B683B51EC746484B9AA90CB481D637BD}

コントロールバーのスタイルは次のとおりです。

<table id="table_681E13F264674F849FAA2523EB65F094"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-control-bar</span> （デフォルトの動作）</td>
   <td colname="col2"> <p>コントロールバーに適用可能 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 機能ボタン {#section_57FFD242FF674EA2867BCF6CA7F6B855}

>[!NOTE]
>
>次の表の文字は、この図の文字に対応しています。

スクラブバーのスタイルを次に示します。

<table id="table_2207AD72E72A47FFA03AC748F06A54FD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル (A) </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar</span> </td> 
   <td colname="col2"> <p>コントロールバーのスクラブバー </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-buffer-progress-bar</span> </td> 
   <td colname="col2"> <p>スクラブバーのバッファープログレスバー </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-seek-to-bar</span> </td> 
   <td colname="col2"> <p>ユーザーがスクラブバーでシークしているときの状態 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-playback-progress-bar</span> </td> 
   <td colname="col2"> <p>通常の再生におけるスクラブバーの状態 </p> </td> 
  </tr>
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-progress-bar-play-head</span> </td>
   <td colname="col2"> <p>再生中にスクラブバーでヘッドを再生 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-ad-marker-bar</span> </td>
   <td colname="col2"> <p>広告マーカーバー </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-ad-marker</span> </td>
   <td colname="col2"> <p>広告マーカー </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。

* `scrubBarBehavior`
* `bufferProgressBarBehavior`
* `playHeadBehavior`
* `playProgressBarBehavior`
* `seekToBarBehavior`

## 再生/一時停止ボタン {#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

再生/一時停止ボタンのスタイルを次に示します。

<table id="table_975C2293222A4782A8C75A6149C1AD27">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (B) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause</span> </td>
   <td colname="col2"> <p>コントロールバーで一時停止ボタンを再生します。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> 一時停止状態で </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-playpause</span> 遊びの状態で </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `playPauseButtonBehavior`.

## 音量 {#section_23E17BD2343948F8A2CEE1C8BEE2F874}

ボリュームボタンを設定するスタイルは次のとおりです。

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (C) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><span class="codeph"> .ptp-volume-control</span>
     <ul id="ul_B12ADDFB83EA40FD8B4E92AF418AA4B4">
      <li id="li_7DA8143A69ED4E7D8A560B9FF75D6BA7"><span class="codeph"> .expanded</span> </li>
      <li id="li_D8CCAD45D81C4850B6903FE261833AE6"><span class="codeph"> .vertical</span> </li>
     </ul> </p> </td>
   <td colname="col2"> <p>コントロールバーのボリュームコントロール
     <ul id="ul_2C60F018FDCB458885738AC378C02F61">
      <li id="li_6B19572B504A4BBF9C97DC29C0E92A1D">コントロールが展開された状態の場合 </li>
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">コントロールが縦方向の形式の場合 </li>
     </ul> </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume</span> </td>
   <td colname="col2"> <p>コントロールバーのボリュームボタン </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.min-volume-state</span> </td>
   <td colname="col2"> <p>ボリュームが最小状態の場合 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-volume.mute-state</span> </td>
   <td colname="col2"> <p>ボリュームがミュート状態の場合 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `volumeBehavior` および `muteButtonBehavior`.

次に、ボリュームスライダのスタイルを示します。

<table id="table_E3DC93F8FC614C30AADAE259D18F10EF">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (D) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-slider</span> </td>
   <td colname="col2"> <p>ボリュームスライダ。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-volume-hidden</span> </td>
   <td colname="col2"> <p>非表示状態のボリュームスライダ。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `volumeSliderBehavior`.

## 巻き戻し {#section_06EE608FC54A4CF5B5DF9DC743CFC740}

巻き戻しボタンのスタイルは次のとおりです。

<table id="table_0ACB116582D54B188E9F5B5C03D3A615">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (E) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>コントロールバーの巻き戻しボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `rewindButtonBehavior`.

## 時間 {#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

残り時間をコントロールバーに表示するスタイルは次のとおりです。

<table id="table_CEE62BFF5FB04FDCBBE1331E0D727EBA">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (F) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-txt-display-time</span> </td>
   <td colname="col2"> <p>残り時間をコントロールバーに表示します </p> </td>
  </tr>
</tbody>
</table>

デフォルトの動作は次のとおりです。 `timeRemainingBehavior`.

## 巻き戻し（速い） {#section_F6E6C65BD3BD493A89915DF9B92933BA}

次に、[ 巻き戻し ] ボタンのスタイルを示します。

<table id="table_25BB4966B709402383AB6A6822FC1999">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (G) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>コントロールバーの [ 巻き戻し ] ボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `fastRewindButtonBehavior`.

## 巻き戻し（遅く） {#section_38A22BB8681B430F8C6808C3BD21FB4E}

次に、[ 巻き戻し ] ボタンのスタイルを示します。

<table id="table_E623C374622A497C91E22333D77AF8F6">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (H) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowrewind</span> </td>
   <td colname="col2"> <p>コントロールバーの [ 巻き戻し ] ボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `slowRewindButtonBehavior`.

## 遅い進み方 {#section_92ACF092EECC4A5EAF6AA090C05E552E}

次に、「ゆっくり進む」ボタンのスタイルを示します。

<table id="table_88C1CF5DB2D84EDBA01AC62B70509B08">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (I) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowforward</span> </td>
   <td colname="col2"> <p>コントロールバーの遅い進むボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `slowForwardButtonBehavior`.

## 早送り {#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

次に、「早送り」ボタンのスタイルを示します。

<table id="table_F166BD1E8B934B34AF3690BBBAD894B7">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル (J) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastforward</span> </td>
   <td colname="col2"> <p>コントロールバーの早送りボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は次のとおりです。 `fastForwardButtonBehavior`.

## オーディオトラック {#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

オーディオトラックを設定するスタイルを次に示します。

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>オーディオトラックボタン (K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>コントロールバーのオーディオトラックボタン。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> audioTrackButtonBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択パネル (L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>オーディオトラックを選択するためのパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> audioTrackSelectionPanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択ヘッダー (M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>のヘッダー <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択メニュー (N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p>メニュー項目 ( <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
 </tbody>
</table>

## 共有 {#section_B2ADC76E76304A68AD648A00A12B676E}

共有を設定するスタイルを次に示します。

<table id="table_3264C472809D462B8FC16680B96B1AC9">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>ソーシャルメディア共有ボタン (O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>コントロールバーのソーシャルメディア共有ボタン（開くボタン） <span class="codeph"> ptp-share-video-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> shareVideoButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>ビデオパネルの共有 (P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>ソーシャル共有オプションを表示するパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> shareVideoPanelBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>ビデオメニューの共有 (Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p>のヘッダー <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>のメニュー <span class="codeph"> ptp-share-video-panel</span> ソーシャルメディアでコンテンツを共有するためのすべてのオプションを表示します。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p>メニュー項目 ( <span class="codeph"> share-video-panel-menu</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>facebookでコンテンツを共有できるメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>twitter上でコンテンツを共有できるメニュー項目。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Google Plus でコンテンツを共有できるメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>linkedInでコンテンツを共有できるメニュー項目です。 </p> </td>
  </tr>
 </tbody>
</table>

## クローズドキャプション {#section_A01BA68218564DA0B7D6BF51F045D7AB}

次に、クローズドキャプションを設定するスタイルを示します。

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションボタン (R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-closed-caption</span> </td>
   <td colname="col2"> <p>The <span class="uicontrol"> クローズドキャプション</span> ボタンをクリックします。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> closedCaptionButtonBehavior</span>. </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-state</span> </td>
   <td colname="col2"> <p>ビデオのキャプションが有効になっている。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションパネル (S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-panel</span> </td>
   <td colname="col2"> <p>クローズドキャプション用のパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> closedCaptionLanguagePanelBehavior</span>. </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプション言語 (T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-panel:</span> </td>
   <td colname="col2"> <p>のヘッダー <span class="codeph"> ptp-audio-track-selection-panel</span>. </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-menu: </span> </td>
   <td colname="col2"> <p>クローズドキャプションパネルのメニュー。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションオプション (U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-btn</span> </td>
   <td colname="col2"> <p>The <span class="uicontrol"> オプション</span> ボタンをクリックします。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-panel</span> </td>
   <td colname="col2"> <p>クローズドキャプションパネルのオプションパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-menu-item</span> </td>
   <td colname="col2"> <p>クローズドキャプションパネルのメニュー項目。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>選択した状態。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-done-btn</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> 完了</span> ボタンをクリックします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-menu</span> </td> 
   <td colname="col2"> <p>クローズドキャプションのオプションメニュー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-main-menu</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションのメインメニュー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-sub-menu</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションのサブメニュー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-opacity-slider</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションの不透明度スライダー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-separator</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションの区切り文字。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-menu-item</span> </td> 
   <td colname="col2"> <p>クローズドキャプション <span class="uicontrol"> オプション</span> メニュー項目。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-preview-panel</span> </td> 
   <td colname="col2"> <p>クローズドキャプションのプレビューパネル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-footer</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションのフッター。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> リセット</span> ボタンをクリックします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-apply-button</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> 適用</span> ボタンをクリックします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> closedCaptionOptionsPanelBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## その他のオプション (V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

次に、追加のオプションを設定するスタイルを示します。
<table id="table_EC6EF88E2EDE4B8EBB1C14F87A6161FA"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> その他のオプション</span> 」ボタンをクリックします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options.ptp-control-bar-btn</span> </td> 
   <td colname="col2"> <p>The <span class="codeph"> ptp-btn-more-options</span> コントロールバーで使用される。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel</span> </td> 
   <td colname="col2"> <p>[ その他のオプション ] コントロールパネル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu</span> </td> 
   <td colname="col2"> <p>[ その他のオプション ] コントロールパネルメニュー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu-item</span> </td> 
   <td colname="col2"> <p>[ その他のオプション ] コントロールパネルのメニュー項目です。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は次のとおりです。 `moreOptionsButtonBehavior`.

## PIP ボタン (W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

これが、 [!UICONTROL PIP<] ボタン：

<table id="table_EE2E882C87E24D39B8D5347686F29E55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-pip</span> </td> 
   <td colname="col2"> <p>コントロールバーの PIP ボタン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> pipButtonBehavior</span>. </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## 全画面表示 (X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

フルスクリーンを設定するスタイルを次に示します。

<table id="table_5941835F31AC4E9CBA9702AB8D813B8F"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-fullscreen</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> 全画面表示</span> ボタンをクリックします。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は次のとおりです。 `fullScreenButtonBehavior`.

## トリック再生 (Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

次に、トリック再生を設定するスタイルを示します。

<table id="table_F1ADAC0A4B4E48669828690BDEB4BC09"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-control-bar-trick-play-rate</span> </td> 
   <td colname="col2"> <p>コントロールバーのトリック率表示コンポーネント。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は次のとおりです。 `trickPlayRateDisplayBehavior`.

## マルチビュー (Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

次に、マルチビューを設定するスタイルを示します。

<table id="table_84B37D7410EE40DFA7A8BB8431C6DCF0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-multiview</span> </td> 
   <td colname="col2"> <p>The <span class="uicontrol"> MultiView</span> ボタンと、 <span class="uicontrol"> Multiview</span> 」ボタンをクリックします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は次のとおりです。 <span class="codeph"> multiViewButtonBehavior</span>. </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## サムネール {#section_0AFD932975634BB08387EEE7D3BFC438}

次に、サムネールを設定するスタイルを示します。

<table id="table_968136A8BBA042A7A8E79739B8F92F55"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-progress-bar-thumb-nail</span> </td> 
   <td colname="col2"> <p>サムネールのプログレスバー。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は次のとおりです。 `thumbnailPreviewBehavior`.

## エラーメッセージ {#section_AC9858EE1B5A4FF4947E383C663B6AB5}

次に、エラーメッセージを設定するスタイルを示します。

<table id="table_7F4C156170DB4AFFA7DEE06F00449506"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel</span> </td> 
   <td colname="col2"> <p>プレーヤーからのエラーメッセージを表示するパネル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-icon</span> </td> 
   <td colname="col2"> <p>エラーメッセージが表示されたときにパネルに表示されるアイコン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-message</span> </td> 
   <td colname="col2"> <p>表示されるエラーメッセージ。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は次のとおりです。 `errorMessagePanelBehavior`.

## バッファリングオーバーレイ {#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

次に、サムネールを設定するスタイルを示します。

<table id="table_1FECE1DC29B8434B886751A29455F004"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-buffering-overlay</span> </td> 
   <td colname="col2"> <p>バッファリングオーバーレイコントロール。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトのオーバーレイは、 `bufferingOverlayBehavior`.

## 特定のセレクター {#section_51F735AEF82E41E890FF59E031A0DB89}

次に、「早送り」ボタンのスタイルを示します。

<table id="table_E77EDC7D227348E79C7E73FB5D46F992"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ad-break</span> </td> 
   <td colname="col2"> <p>広告の再生中のコントロールパネルの状態。 </p> <p>次の場合に適用されます。 
     <ul id="ul_D5076303DCD94D968682289823D1A9F2"> 
      <li id="li_4290C4B2D48546E3AD023BED6CAAE395"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_72A3D3E916E44A55BA170407EAB0527D"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_A0BAEBB0E01B402EB83E3CE9B92B15CC"><span class="codeph"> .ptp-btn-fastrewind</span> </li> 
      <li id="li_FDF2CEDB0A854098907FF9CBCF1A61C1"><span class="codeph"> .ptp-btn-slowforward</span> </li> 
      <li id="li_CD2E14DB3DD64C10A253DA23FBE04A04"><span class="codeph"> .ptp-btn-slowforward</span> </li> 
      <li id="li_A230359E8F7F4571A9EBFF0E4C2462D7"><span class="codeph"> .ptp-btn-slowrewind</span> </li> 
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-more-options </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-closed-caption </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-scrub-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-seek-to-bar</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-view</span> </td> 
   <td colname="col2"> <p>マルチビュー内のコントロールの状態。 </p> <p>次の場合に適用されます。 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-closed-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-state</span> </td> 
   <td colname="col2"> <p>プレーヤーはフルスクリーンモードになっています。 </p> <p>次の場合に適用されます。 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>
