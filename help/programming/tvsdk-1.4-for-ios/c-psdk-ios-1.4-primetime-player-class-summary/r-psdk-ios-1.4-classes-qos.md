---
description: プレイヤーのパフォーマンスを判断するのに役立つ情報を提供するクラスです。
title: QoSクラス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# QoSクラス{#qos-classes}

プレイヤーのパフォーマンスを判断するのに役立つ情報を提供するクラスです。

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> 名前 </th> 
   <th colname="2" class="entry"> 説明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
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
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTPlaybackInformation.html" format="html" scope="external"> PTPlaybackInformation</a> </td> 
   <td colname="2"> 再生の実行方法に関する情報を提供します。 フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリング試行回数、最初のビデオフラグメントからの最初のバイト取得に要した時間、最初のフレームのレンダリングに要した時間、現在のバッファ長、バッファ時間などが含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      再生とデバイスの両方に不可欠なQoS指標を提供します。
    </pre>
    <pre>
      QOS情報プロバイダークラス。
    </pre> </td> 
  </tr> 
 </tbody> 
</table>

