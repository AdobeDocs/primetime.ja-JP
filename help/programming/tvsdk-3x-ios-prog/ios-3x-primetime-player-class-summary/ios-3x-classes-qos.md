---
description: これらのクラスは、プレーヤーのパフォーマンスを判断するのに役立つ情報を提供します。
title: QoS クラス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# QoS クラス {#qos-classes}

これらのクラスは、プレーヤーのパフォーマンスを判断するのに役立つ情報を提供します。

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>名前</b></th> 
   <th colname="2" class="entry"><b>説明</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
   <td colname="2">TVSDK が実行されるプラットフォームとオペレーティングシステムに関する情報を提供します。 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">プラットフォーム OS のバージョン </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">TVSDK ライブラリのバージョン番号 </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">デバイスのモデル名 </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">デバイスの製造元名 </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">デバイスの UUID </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">デバイス画面の幅/高さ </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTPlaybackInformation.html" format="html" scope="external"> PTPlaybackInformation</a> </td> 
   <td colname="2"> 再生の実行方法に関する情報を提供します。 これには、フレームレート、プロファイルビットレート、バッファリングに費やした合計時間、バッファリングの試行回数、最初のビデオフラグメントから最初のバイトを取得するのに要した時間、最初のフレームのレンダリングに要した時間、現在のバッファ長、バッファ時間が含まれます。 </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      再生とデバイスの両方に不可欠な QoS 指標を提供します。
    </pre>
    <pre>
      QOS 情報プロバイダークラス。
    </pre> </td> 
  </tr> 
 </tbody> 
</table>
