---
description: これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。
seo-description: これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。
seo-title: QoSクラス
title: QoSクラス
uuid: c1192474-d183-4995-87ef-839699844b48
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# QoSクラス {#qos-classes}

これらのクラスは、プレイヤーのパフォーマンスを判断するのに役立つ情報を提供します。

パッケージ： [com.adobe.mediacore.qos](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/package-detail.html) Package: [com.adobe.mediacore.qos.metrics](https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/package-detail.html)

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/BufferingMetrics.html" format="html" scope="external"> BufferingMetrics</a></span> </td> 
   <td colname="2"> プレーヤーがバッファリングに費やした時間と、バッファリングイベントが発生した頻度に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/DeviceInformation.html" format="html" scope="external"> DeviceInformation</a></span> </td> 
   <td colname="2">TVSDKが実行されるプラットフォームとオペレーティングシステムに関する情報を提供します。 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">プラットフォームOSのバージョン </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">TVSDKライブラリのバージョン番号 </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">デバイスのモデル名 </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">デバイスの製造元名 </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">デバイスのUUID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">デバイス画面の幅/高さ </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/LoadInformation.html" format="html" scope="external"> LoadInformation</a></span> </td> 
   <td colname="2"> 様々なリソース（ファイル、マニフェストまたはプレイリスト、フラグメント/セグメント、トラックなど）の読み込みに関する様々なQoS情報が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/LoadInformationType.html" format="html" scope="external"> LoadInformationType</a></span> </td> 
   <td colname="2"> LoadInformationオブジェクトのtypeプロパティで使用可能な値をリストする列挙クラス。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/PlaybackInformation.html" format="html" scope="external"> PlaybackInformation</a></span> </td> 
   <td colname="2"> 再生の実行方法に関する情報を提供します。 これには、フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリングの試行回数、最初のビデオフラグメントから最初のバイトを取得するのにかかった時間、最初のフレームのレンダリングにかかった時間、現在のバッファ長、バッファ時間が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackLoadMetrics</a></span> </td> 
   <td colname="2"> メディアの読み込みに要した時間、プレーヤーが最初のフレームをレンダリングするのに要した時間、エラーが発生した場合に失敗した時間に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackMetrics.html" format="html" scope="external"> PlaybackMetrics</a></span> </td> 
   <td colname="2"> 再生動作に関する情報を提供します。 フレームレート、ビットレート、バッファー長などが含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/metrics/PlaybackSessionMetrics.html" format="html" scope="external"> PlaybackSessionMetrics</a></span> </td> 
   <td colname="2"> プレイヤーが実際に再生に費やした時間（秒）と、ビデオが実際に画面に表示されていた時間に関する情報を提供します。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/asdoc-dhls_1.4/com/adobe/mediacore/qos/QOSProvider.html" format="html" scope="external"> QOSProvider</a></span> </td> 
   <td colname="2">
    <ph>
      再生とデバイスの両方に不可欠なQoS指標を提供します。
    </ph>
    <ph>
      QOS情報プロバイダークラス。
    </ph> </td> 
  </tr> 
 </tbody> 
</table>

