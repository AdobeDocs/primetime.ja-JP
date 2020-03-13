---
description: これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。
seo-description: これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。
seo-title: QoSクラス
title: QoSクラス
uuid: c1f0218d-4a79-4141-9a74-e70ac4f70aa5
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# QoSクラス {#qos-classes}

これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。

パッケージ： [com.adobe.mediacore.qos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/package-summary.html) Package: [com.adobe.mediacore.qos.metrics](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">指標を参照してください。<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/BufferingMetrics.html" format="html" scope="external"> BufferingMetrics</a></span></td> 
   <td colname="2"> プレーヤーがバッファリングに費やした時間と、バッファリングイベントが発生した頻度に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/DeviceInformation.html" format="html" scope="external"> DeviceInformation</a> </span></td> 
   <td colname="2">フレーズを実行するプラットフォームとオペレーティングシステムに関する情報を提供します。 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">プラットフォームOSのバージョン </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">フレーズライブラリのバージョン番号 </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">デバイスのモデル名 </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">デバイスの製造元名 </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">デバイスのUUID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">デバイス画面の幅/高さ </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/LoadInfo.html" format="html" scope="external"> LoadInfo</a></span> </td> 
   <td colname="2"> 様々なリソース（ファイル、マニフェストまたはプレイリスト、フラグメント/セグメント、トラックなど）の読み込みに関する様々なQoS情報が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/PlaybackInformation.html" format="html" scope="external"> PlaybackInformation</a></span> </td> 
   <td colname="2"> 再生の実行方法に関する情報を提供します。 これには、フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリングの試行回数、最初のビデオフラグメントから最初のバイトを取得するのにかかった時間、最初のフレームのレンダリングにかかった時間、現在のバッファ長、バッファ時間が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">指標を参照してください。<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackLoadMetrics</a></span> </td> 
   <td colname="2"> メディアの読み込みに要した時間、プレーヤーが最初のフレームをレンダリングするのに要した時間、エラーが発生した場合に失敗した時間に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">指標を参照してください。<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackMetrics</a> </span></td> 
   <td colname="2"> 再生動作に関する情報を提供します。 フレームレート、ビットレート、バッファー長などが含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">指標を参照してください。<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackSessionMetrics.html" format="html" scope="external"> PlaybackSessionMetrics</a></span> </td> 
   <td colname="2"> プレイヤーが実際に再生に費やした時間（秒）と、ビデオが実際に画面に表示されていた時間に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/QOSProvider.html" format="html" scope="external"> QOSProvider</a></span></td> 
   <td colname="2">再生とデバイスの両方に不可欠なQoS指標を提供します。 QOS情報プロバイダークラス。</td> 
  </tr> 
 </tbody> 
</table>
