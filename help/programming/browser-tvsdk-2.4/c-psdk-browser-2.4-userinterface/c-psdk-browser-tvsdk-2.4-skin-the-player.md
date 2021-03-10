---
description: 次の情報を使用して、プレイヤーのスキン設定を行うことができます。 各ビジュアル構成体に対して、対応する動作がデフォルトの動作で言及されます。
title: プレイヤーのスキン表示
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 0%

---


# プレイヤーのスキン表示{#skinning-the-player}

次の情報を使用して、プレイヤーのスキン設定を行うことができます。 各ビジュアル構成体に対して、対応する動作がデフォルトの動作で言及されます。

>[!IMPORTANT]
>
>このドキュメントのスキン表示の詳細は、UIフレームワークで作成されるデフォルトのUI要素です。 プレイヤーがこれらの要素を変更した場合は、スキン表示要素も変更する必要があります。

## コンテナdivs {#section_99B0D598219D4150B57E97D5381B118F}

コンテナdivのスタイルを次に示します。

>[!TIP]
>
>これらのdivは`common-styles.css`ファイルに一覧表示されます。

メインdivのスタイルを次に示します。

<table id="table_AC5745DF725543ADBBCD68BA6130DF12"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><b>メインDiv</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-main-video-div-style</span> </td> 
   <td colname="col2"> <p>ビデオを再生するメインdivのスタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .pip-mode-active</span> </td> 
   <td colname="col2"> <p>PIPモードがアクティブな場合に使用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は<span class="codeph"> videoBehavior</span>です。 </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>ピクチャインピクチャ(PIP)</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-pip-video-div</span> </td> 
   <td colname="col2"> <p>PIPビデオが再生されるdivのスタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .表示 — メインビデオ</span> </td> 
   <td colname="col2"> <p>スワップされ、メインビデオとして表示される場合に、初期PIPに適用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><b>マルチビデオ表示</b> </p> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-表示-コンテナ</span> </td> 
   <td colname="col2"> <p>マルチビデオ表示で使用されます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-multi-表示-表示</span> </td> 
   <td colname="col2"> <p>マルチビュー内の各ビデオに配置される共通のcssスタイル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multiview</span> </td> 
   <td colname="col2"> <p>マルチビューで各ビデオを格納するコンテナがマルチビューの場合。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 各種コントロール{#section_E9E4A8E3AEBF4BDC89840B84B3B0E737}

汎用プレーヤーコントロールのスタイルを次に示します。

>[!TIP]
>
>これらのスタイルは`default-controls.css`ファイルに一覧表示されます。

<table id="table_0ACB6BAB5DAD42DBBD18CA7C0385A261"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp制御</span> </td> 
   <td colname="col2"> <p>スクラバーとスペースを除く、コントロールバーのすべてのコントロールに適用できます </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-input-slider</span> </td> 
   <td colname="col2"> <p>入力スライダ </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-panel-header</span> </td> 
   <td colname="col2"> <p>パネルのヘッダー </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-vertical-リスト-menu-item</span> </td> 
   <td colname="col2"> <p>縦書きスタイルのメニューリスト </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-fill-spacer</span> </td> 
   <td colname="col2"> <p>コントロールバーのスペース </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-hr-separator</span> </td> 
   <td colname="col2"> <p>区切り線（横） </p> </td> 
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

## コントロールバー{#section_B683B51EC746484B9AA90CB481D637BD}

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

## 機能ボタン{#section_57FFD242FF674EA2867BCF6CA7F6B855}

>[!NOTE]
>
>次の表に示す文字は、この図の文字に対応しています。

スクラブバーのスタイルは次のとおりです。

<table id="table_2207AD72E72A47FFA03AC748F06A54FD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> スタイル(A) </th> 
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
   <td colname="col2"> <p>ユーザーがスクラブバー上でシークしている場合の状態 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-scrub-bar .ptp-playback-progress-bar</span> </td> 
   <td colname="col2"> <p>通常再生時のスクラブバーの状態 </p> </td> 
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

## 再生/一時停止ボタン{#section_F1F40A948D0049C5A4D8EA5F2A475CAA}

再生/一時停止ボタンのスタイルは次のとおりです。

<table id="table_975C2293222A4782A8C75A6149C1AD27">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(B) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause</span> </td>
   <td colname="col2"> <p>コントロールバーの再生/一時停止ボタン。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td>
   <td colname="col2"> <p><span class="codeph"> pause状態のptp-btn-</span> playpause </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> ptp-btn-playpause.pause-state</span> </td> 
   <td colname="col2"> <p><span class="codeph"> ptp-btn-</span> playpause（再生状態） </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は`playPauseButtonBehavior`です。

## ボリューム{#section_23E17BD2343948F8A2CEE1C8BEE2F874}

ボリュームボタンを設定するスタイルを次に示します。

<table id="table_8F9831F36A4D427CA31C9FFA4173170D">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(C) </th>
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
      <li id="li_6489E422E1944D5194CBDFC8383D2F30">コントロールが縦置きの場合 </li>
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

デフォルトの動作は`volumeBehavior`と`muteButtonBehavior`です。

ボリュームスライダのスタイルを次に示します。

<table id="table_E3DC93F8FC614C30AADAE259D18F10EF">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(D) </th>
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
   <td colname="col2"> <p>非表示状態のボリュームスライダー。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は`volumeSliderBehavior`です。

## 巻き戻し{#section_06EE608FC54A4CF5B5DF9DC743CFC740}

巻き戻しボタンのスタイルは次のとおりです。

<table id="table_0ACB116582D54B188E9F5B5C03D3A615">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(E) </th>
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

デフォルトの動作は`rewindButtonBehavior`です。

## 時刻{#section_0E6549B3DF6D4C10947D445A5F8EEA7F}

コントロールバーに残りの時間を表示するスタイルは次のとおりです。

<table id="table_CEE62BFF5FB04FDCBBE1331E0D727EBA">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(F) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-txt-display-time</span> </td>
   <td colname="col2"> <p>コントロールバーに残りの時間を表示します。 </p> </td>
  </tr>
</tbody>
</table>

デフォルトの動作は`timeRemainingBehavior`です。

## 早戻し{#section_F6E6C65BD3BD493A89915DF9B92933BA}

「早戻し」ボタンのスタイルは次のとおりです。

<table id="table_25BB4966B709402383AB6A6822FC1999">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(G) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-fastrewind</span> </td>
   <td colname="col2"> <p>コントロールバーの早戻しボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は`fastRewindButtonBehavior`です。

## 遅い巻き戻し{#section_38A22BB8681B430F8C6808C3BD21FB4E}

[巻き戻しを遅くする]ボタンのスタイルを次に示します。

<table id="table_E623C374622A497C91E22333D77AF8F6">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(H) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowrewind</span> </td>
   <td colname="col2"> <p>コントロールバーの巻き戻し（遅く）ボタン。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は`slowRewindButtonBehavior`です。

## 遅送り{#section_92ACF092EECC4A5EAF6AA090C05E552E}

次に、スローフォワードボタンのスタイルを示します。

<table id="table_88C1CF5DB2D84EDBA01AC62B70509B08">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(I) </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-slowforward</span> </td>
   <td colname="col2"> <p>コントロールバーの遅い進むボタンです。 </p> </td>
  </tr>
 </tbody>
</table>

デフォルトの動作は`slowForwardButtonBehavior`です。

## 早送り{#section_F90ED8B3739B49ACAB1F12DF18F0E4D6}

次に、早送りボタンのスタイルを示します。

<table id="table_F166BD1E8B934B34AF3690BBBAD894B7">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル(J) </th>
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

デフォルトの動作は`fastForwardButtonBehavior`です。

## オーディオトラック{#section_1CDF4FA5A1C14DB6B9C96579FFA1057C}

オーディオトラックを設定するスタイルは次のとおりです。

<table id="table_22FC521D786B45EB84F230894FFECE79">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th> 
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>オーディオトラックボタン(K)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-audio-track</span> </td>
   <td colname="col2"> <p>コントロールバーのオーディオトラックボタン。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> audioTrackButtonBehavior</span>です。 </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択パネル(L)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-panel</span> </td> 
   <td colname="col2"> <p>オーディオトラックを選択するためのパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> audioTrackSelectionPanelBehavior</span>です。 </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択ヘッダー(M)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-audio-track-selection-panel</span>のヘッダーです。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>オーディオトラック選択メニュー(N)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-menu</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-audio-track-selection-panel</span>のメニュー項目です。 </p> </td>
  </tr>
 </tbody>
</table>

## 共有{#section_B2ADC76E76304A68AD648A00A12B676E}

共有を設定するスタイルは次のとおりです。

<table id="table_3264C472809D462B8FC16680B96B1AC9">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>ソーシャルメディア共有ボタン(O)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video</span> </td> 
   <td colname="col2"> <p>コントロールバーのソーシャルメディア共有ボタンで、<span class="codeph"> ptp-share-video-panel</span>が開きます。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> shareVideoButtonBehavior</span>です。 </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>ビデオパネルの共有(P)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel</span> </td>
   <td colname="col2"> <p>ソーシャル共有オプションを表示するパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> shareVideoPanelBehavior</span>です。 </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>ビデオメニューの共有(Q)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-audio-track-selection-header</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-audio-track-selection-panel</span>のヘッダーです。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .share-video-panel-menu</span> </td>
   <td colname="col2"> <p>ソーシャルメディアでコンテンツを共有するためのすべてのオプションを表示する、<span class="codeph">ptp-share-video-panel</span>のメニュー。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-share-video-panel-menu-item</span> </td>
   <td colname="col2"> <p><span class="codeph"> share-video-panel-menu</span>内のメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-facebook</span> </td>
   <td colname="col2"> <p>Facebookでコンテンツを共有するためのメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-twitter</span> </td>
   <td colname="col2"> <p>Twitterでコンテンツを共有するためのメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-google-plus</span> </td>
   <td colname="col2"> <p>Google Plusでコンテンツを共有するためのメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-share-video-linkedin</span> </td>
   <td colname="col2"> <p>LinkedInでコンテンツを共有するためのメニュー項目です。 </p> </td>
  </tr>
 </tbody>
</table>

## クローズドキャプション{#section_A01BA68218564DA0B7D6BF51F045D7AB}

クローズドキャプションを設定するスタイルを次に示します。

<table id="table_777C7034C9424F8C841DABD480FFAC47">
 <thead>
  <tr>
   <th colname="col1" class="entry"> スタイル </th>
   <th colname="col2" class="entry"> 説明 </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションボタン(R)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-btn-closed-caption</span> </td>
   <td colname="col2"> <p>コントロールバーの「<span class="uicontrol">クローズドキャプション</span>」ボタン。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> closedCaptionButtonBehavior</span>です。 </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .on-state</span> </td>
   <td colname="col2"> <p>キャプションはビデオに対して有効になっています。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションパネル(S)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-panel</span> </td>
   <td colname="col2"> <p>クローズドキャプションのパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1">デフォルトの動作は<span class="codeph"> closedCaptionLanguagePanelBehavior</span>です。 </td>
   <td colname="col2"> </td>
</tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションの言語(T)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-panel:</span> </td>
   <td colname="col2"> <p><span class="codeph"> ptp-audio-track-selection-panel</span>のヘッダーです。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-language-menu:  </span> </td>
   <td colname="col2"> <p>クローズドキャプションパネルのメニュー。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"> <p><b>クローズドキャプションオプション(U)</b> </p> </td>
   <td colname="col2"> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-btn</span> </td>
   <td colname="col2"> <p>クローズドキャプションオプションパネルの「<span class="uicontrol">オプション</span>」ボタン。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-options-panel</span> </td>
   <td colname="col2"> <p>クローズドキャプションパネルのオプションパネル。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-menu-item</span> </td>
   <td colname="col2"> <p>クローズドキャプションパネル内のメニュー項目です。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .selected</span> </td>
   <td colname="col2"> <p>選択状態。 </p> </td>
  </tr>
  <tr>
   <td colname="col1"><span class="codeph"> .ptp-closed-caption-done-btn</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションパネルのヘッダーにある「<span class="uicontrol">完了</span>」ボタン。 </p> </td> 
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
   <td colname="col2"> <p>クローズドキャプション<span class="uicontrol">オプション</span>メニュー項目。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-プレビューパネル</span> </td> 
   <td colname="col2"> <p>クローズドキャプションプレビューパネル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-footer</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションのフッター。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-reset-button</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションパネルのフッターにある「<span class="uicontrol">リセット</span>」ボタン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> ptp-closed-caption-options-apply-button</span> </td> 
   <td colname="col2"> <p>クローズドキャプションオプションパネルのフッターにある「<span class="uicontrol">適用</span>」ボタン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は<span class="codeph"> closedCaptionOptionsPanelBehavior</span>です。 </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## その他のオプション(V) {#section_18E25CF8A8964FFD9026A8A833089CE3}

その他のオプションを設定するスタイルは次のとおりです。
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
   <td colname="col2"> <p>「<span class="uicontrol">詳細オプション</span>」ボタン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-btn-more-options.ptp-control-bar-btn</span> </td> 
   <td colname="col2"> <p>コントロールバーで使用する<span class="codeph"> ptp-btn-more-options</span>です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel</span> </td> 
   <td colname="col2"> <p>[その他のオプション]コントロールパネル。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu</span> </td> 
   <td colname="col2"> <p>[その他のオプション]コントロールパネルメニュー。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-more-options-control-panel-menu-item</span> </td> 
   <td colname="col2"> <p>[その他のオプション]コントロールパネルのメニュー項目 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は`moreOptionsButtonBehavior`です。

## PIPボタン(W) {#section_1EE039DEA99541D391B30BD1DF72A83E}

[!UICONTROL PIP<]ボタンのスタイルは次のようになります。

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
   <td colname="col2"> <p>コントロールバーのPIPボタン。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は<span class="codeph"> pipButtonBehavior</span>です。 </td> 
   <td colname="col2"> </td>
  </tr> 
 </tbody> 
</table>

## フルスクリーン(X) {#section_158A19DFB30E4432A67E4A74A7CBA563}

フルスクリーンを設定するスタイルは次のとおりです。

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
   <td colname="col2"> <p>コントロールバーの<span class="uicontrol">フルスクリーン</span>ボタン。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は`fullScreenButtonBehavior`です。

## トリック再生(Y) {#section_AE6F83BB7EE2497FB13CD94A8316192D}

トリック再生を設定するスタイルを次に示します。

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
   <td colname="col2"> <p>コントロールバーのトリックレート表示コンポーネント。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は`trickPlayRateDisplayBehavior`です。

## マルチビュー(Z) {#section_58EFAE7263BA45D3A4E2AB7309A9CAA7}

マルチビューを設定するスタイルは次のとおりです。

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
   <td colname="col2"> <p>コントロールバーの<span class="uicontrol"> MultiView</span>ボタンと、<span class="uicontrol"> Multiview</span>ボタンの初期状態。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1">デフォルトの動作は<span class="codeph"> multiViewButtonBehavior</span>です。 </td> 
   <td colname="col2"> </td> 
  </tr> 
 </tbody> 
</table>

## サムネール{#section_0AFD932975634BB08387EEE7D3BFC438}

サムネールを設定するスタイルは次のとおりです。

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

デフォルトの動作は`thumbnailPreviewBehavior`です。

## エラーメッセージ{#section_AC9858EE1B5A4FF4947E383C663B6AB5}

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
   <td colname="col2"> <p>プレイヤーからのエラーメッセージを表示するパネルです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-icon</span> </td> 
   <td colname="col2"> <p>エラーメッセージが表示された場合にパネルに表示されるアイコンです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .ptp-error-message-panel-message</span> </td> 
   <td colname="col2"> <p>表示されるエラーメッセージです。 </p> </td> 
  </tr> 
 </tbody> 
</table>

デフォルトの動作は`errorMessagePanelBehavior`です。

## バッファリングオーバーレイ{#section_2FE8FDE2599E42BAA7411D0D38FA0A88}

サムネールを設定するスタイルは次のとおりです。

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

デフォルトのオーバーレイは`bufferingOverlayBehavior`です。

## 特定のセレクター{#section_51F735AEF82E41E890FF59E031A0DB89}

次に、早送りボタンのスタイルを示します。

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
      <li id="li_5711A315872F4FA59FDDF0EF0AFD03C6"><span class="codeph"> .ptp-btn-more-options  </span> </li> 
      <li id="li_71C8E76077A84ED590160AB5ABFCC0D7"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_4A3113C0360F4F708AAA96AB316FA057"><span class="codeph"> .ptp-btn-closed-caption  </span> </li> 
      <li id="li_901A0186D65A48A1B774DC555CEC5367"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
      <li id="li_2331583C01C2482B8EE72979FBF111DB"><span class="codeph"> .ptp-btn-pip  </span> </li> 
      <li id="li_7BB39BDF5E294AEB8FA3DCD9F9A29468"><span class="codeph"> .ptp-btn-rewind</span> </li> 
      <li id="li_E4FEF5A7486A40F6A5FE1119BD63AFEF"><span class="codeph"> .ptp-scrub-bar</span> </li> 
      <li id="li_12153547558A4871842EE0416BCCA8B2"><span class="codeph"> .ptp-seek-to-bar</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .multi-表示</span> </td> 
   <td colname="col2"> <p>マルチビュー中のコントロールの状態。 </p> <p>次の場合に適用されます。 
     <ul id="ul_A8AC653C30814AC49041F3B58A2106F4"> 
      <li id="li_0407167DA21647A8A6960DFE55A33F42"><span class="codeph"> .ptp-btn-fastforward</span> </li> 
      <li id="li_EA71CAF41CDC41DE859A85CE482BE97C"><span class="codeph"> .ptp-btn-share-video</span> </li> 
      <li id="li_F3A998C51A034C22A914EAEFF19FFEA7"><span class="codeph"> .ptp-btn-closed-caption</span> </li> 
      <li id="li_022F871ABC894C9BA879B3AF3D341202"><span class="codeph"> .ptp-btn-audio-track</span> </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> .fullscreen-state</span> </td> 
   <td colname="col2"> <p>プレイヤーはフルスクリーンモードです。 </p> <p>次の場合に適用されます。 
     <ul id="ul_B235C1D339F64B2FAC6BC72F03807616"> 
      <li id="li_6E050EE74C604FDAB4C9C0447F547A9D"><span class="codeph"> .ptp-control-bar  </span> </li> 
      <li id="li_67D54B1A41764B2DA544479CDA1C901C"><span class="codeph"> .ptp-btn-fullscreen</span> </li> 
     </ul> </p> </td> 
  </tr> 
 </tbody> 
</table>