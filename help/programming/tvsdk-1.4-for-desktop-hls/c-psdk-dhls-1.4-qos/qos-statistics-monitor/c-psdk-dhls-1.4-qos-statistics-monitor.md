---
description: サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。
title: サービス品質の統計
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# サービス品質の統計 {#quality-of-service-statistics}

サービス品質 (QoS) により、ビデオエンジンのパフォーマンスに関する詳細な情報が得られます。 TVSDK は、再生、バッファリング、デバイスに関する詳細な統計情報を提供します。

TVSDK は、以下のダウンロードされたリソースに関する情報も提供します。

* プレイリスト/マニフェストファイル
* ファイルフラグメント
* ファイルのトラッキング情報

## 読み込み情報を使用してフラグメントレベルで追跡 {#track-at-the-fragment-level-using-load-information}

LoadInformation クラスから、フラグメントやトラックなど、ダウンロードされたリソースに関する Quality of Service(QoS) 情報を読み取ることができます。

1. の実装 `onLoadInformationAvailable` コールバックイベントリスナー。

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. フラグメントがダウンロードされるたびに TVSDK が呼び出すイベントリスナーを登録します。

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. 関心のあるデータを `LoadInformation` コールバックに渡される

   <table id="table_75E61A2EB25E435DB631166A7FF64757"> 
   <thead> 
   <tr> 
      <th colname="col01" class="entry"> プロパティ </th> 
      <th colname="col1" class="entry"> タイプ </th> 
      <th colname="col2" class="entry"> 説明 </th> 
   </tr> 
   </thead>
   <tbody> 
   <tr> 
      <td colname="col01"> <span class="codeph"> downloadDuration </span> </td> 
      <td colname="col1"> <p>数値 </p> </td> 
      <td colname="col2"> <p>ダウンロードの時間（ミリ秒）。 </p> <p>TVSDK は、クライアントがサーバーに接続するのに要した時間と、フラグメント全体のダウンロードに要した時間を区別しません。 例えば、10 MB のセグメントのダウンロードに 8 秒かかる場合、 TVSDK はその情報を提供しますが、最初のバイトまで 4 秒かかり、フラグメント全体のダウンロードに 4 秒かかったとは通知しません。 </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>数値 </p> </td> 
      <td colname="col2"> ダウンロードされたフラグメントのメディア時間（ミリ秒）。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> サイズ </span> </td> 
      <td colname="col1"> <p>数値 </p> </td> 
      <td colname="col2"> ダウンロードされたリソースのサイズ（バイト単位）。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> 対応するトラックのインデックス（わかっている場合）。それ以外の場合は 0。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> 対応するトラックの名前（わかっている場合）。それ以外の場合は null。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> 対応するトラックのタイプ（わかっている場合）。それ以外の場合は null。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> TVSDK がダウンロードした内容。 次のいずれかを実行します。 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST — プレイリスト/マニフェスト </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">フラグメント — フラグメント </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK — 特定のトラックに関連付けられたフラグメント </li> 
      </ul> リソースのタイプを検出できない場合があります。 この場合、FILE が返されます。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> ダウンロードされたリソースを指す URL。 </td> 
   </tr> 
   </tbody> 
   </table>

## 再生、バッファリング、デバイスに関する QOS 統計の読み取り {#read-qos-playback-buffering-and-device-statistics}

QOSProvider クラスから、再生、バッファリング、デバイスの統計を読み取ることができます。

The `QOSProvider` クラスは、バッファリング、ビットレート、フレームレート、時間データなどに関する情報を含む様々な統計を提供します。

また、製造元、モデル、オペレーティングシステム、SDK バージョン、画面サイズ/密度など、デバイスに関する情報も提供します。

1. メディアプレーヤーをインスタンス化します。
1. の作成 `QOSProvider` オブジェクトを探し、メディアプレーヤーに接続します。

   ```
   // Create Media Player. 
   _mediaQosProvider = new QOSProvider; 
   _mediaQosProvider.attachMediaPlayer(_mediaPlayer);
   ```

1. （オプション）再生統計を読み取ります。

   再生統計を読み取る 1 つの方法は、タイマーを使用することです。タイマーは、 `QOSProvider`. 例：

   ```
   var qosTimer:Timer = new Timer(1000); // every 1 second  
   qosTimer.addEventListener(TimerEvent.Timer, onQoSTimer);  
   qosTimer.start(); 
   private function onQoSTimer(event:TimerEvent):void { 
       var playbackInformation:PlaybackInformation = _mediaQosProvider.getPlaybackInformation(); 
       qosInfo["Frame rate"] = playbackInformation.frameRate.toFixed();  
       qosInfo["Dropped frames"] = playbackInformation.droppedFrameCount.toFixed(); 
       qosInfo["Bitrate"] = playbackInformation.bitrate.toFixed(); 
       qosInfo["Bandwidth"] = playbackInformation.perceivedBandwidth; 
       qosInfo["Buffering time"] = playbackInformation.bufferingTime.toFixed(); 
       qosInfo["Buffer length"] = playbackInformation.bufferLength.toFixed();  
       qosInfo["Buffer time"] = playbackInformation.bufferTime.toFixed(); 
       qosInfo["Empty buffer count"] = playbackInformation.emptyBufferCount.toFixed();  
       qosInfo["Time to load"] = playbackInformation.timeToLoad.toFixed();  
       qosInfo["Time to start"] = playbackInformation.timeToStart.toFixed(); 
       qosView.update(qosInfo); 
   }
   ```

1. （オプション）デバイス固有の情報を読み取ります。

   ```
   // Show device information 
   var deviceInfo:DeviceInformation = new QOSProvider.deviceInformation; 
   qosInfo["deviceModel"] = deviceInfo.manufacturer +"-" + deviceInfo.model; 
   qosInfo["os"] = deviceInfo.os;  
   qosInfo["runtime"] = deviceInfo.runtimeVersion;  
   qosInfo["widthPixels"] = deviceInfo.widthPixels;  
   qosInfo["heightPixels"] = deviceInfo.heightPixels; 
   qosView.update(qosInfo); 
   ```
