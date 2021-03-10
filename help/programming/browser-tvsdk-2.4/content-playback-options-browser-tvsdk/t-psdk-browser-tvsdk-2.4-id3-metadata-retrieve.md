---
description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 ブラウザーTVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。
title: ID3タグ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# ID3タグ{#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 ブラウザーTVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。

基になるHLSストリームに新しいID3メタデータが見つかると、Browser TVSDKは`AdobePSDK.TimedMetadataEvent`イベントをトリガーします。

ID3の`TimedMetadata`オブジェクトには次のプロパティがあります。

<table id="table_6C61886187FB44B4B9821E4B00200018"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プロパティ名 </th> 
   <th colname="col2" class="entry"> 詳細 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> type  </span> </p> </td> 
   <td colname="col2"> <p><span class="codeph"> TimedMetadata </span>オブジェクトのタイプです。 </p> <p>ID3メタデータの場合、値は<span class="codeph"> AdobePSDK.TimedMetadataType.ID3 </span>です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> time  </span> </p> </td> 
   <td colname="col2"> <p> この時間指定メタデータが検出されたプレイヤーの時間。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id  </span> </p> </td> 
   <td colname="col2"> <p><span class="codeph"> TimedMetadata </span>オブジェクトのID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> name </span> </p> </td> 
   <td colname="col2"> <p><span class="codeph"> TimedMetadata </span>オブジェクトの名前。 ID3メタデータの場合、値は「ID3」です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> content  </span> </p> </td> 
   <td colname="col2"> <p>時間指定メタデータコンテンツ。 ID3タグの場合、この値はシリアライズされたバイト配列を表します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> metadata  </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> TimedMetadata </span> 処理済み情報。 <span class="codeph"> AdobePSDK.Metadataのインスタンスで、ID3フレーム </span> が保存されます。 </p> <p> <p>注意： Safari <span class="codeph">ビデオ</span>タグでは、ID3タグの特定のフレームデータが<span class="codeph"> AdobePSDK.Metadata </span>オブジェクトを介してオブジェクトの形式で公開され、その他のブラウザでは、ID3タグのフレームデータが<span class="codeph"> AdobePSDK.Metadataを介してバイト配列の形式で公開されます/&gt;オブジェクト。</span> </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

`TimedMetadata`に保存されている様々なID3タグは、次の2つの方法でアプリケーションによって取得できます。

* AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLEイベントリスナー内。

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var mediaPlayer = new AdobePSDK.MediaPlayer(); 
   mediaPlayer.addEventListener( AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE ,function(event){ 
       var td = event.timedMetadata; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   }); 
   ```

* `MediaPlayerItem`の`timedMetadata`プロパティを使用します。

   ```
   var isSafari = function () { 
       var nAgt = navigator.userAgent; 
       var appName = navigator.appName; 
       if ((nAgt.indexOf('MSIE') === -1) && //is not MS IE 
           (appName !== 'Netscape' || nAgt.indexOf('Trident/') === -1) && //is not MS IE11 
           (appName !== 'Netscape' || nAgt.indexOf('Edge') === -1) && // is not edge 
           (nAgt.indexOf('Chrome') === -1) && // is not chrome 
           (nAgt.indexOf('Safari') !== -1) //is Safari 
       ){ 
           return true; 
       } 
       return false; 
   }; 
   var hex2a = function (hex, offset, max) { 
       var str = ''; 
       if (!hex) 
           return str; 
       for (var i = offset; i < hex.length && i < offset + max; i++) 
           str += String.fromCharCode(hex[i]); 
       return str; 
   }; 
   var timedMetadataList = player.currentItem.timedMetadata; 
   for(var i = 0; i < timedMetadataList.length; i++){ 
       var td = timedMetadataList[i]; 
       if(td.type == AdobePSDK.TimedMetadataType.ID3){ 
           var md = td.metadata; 
           var keySet = md.keySet; 
           var onSafari = isSafari(); 
           if(keySet && keySet.length){ 
               var msg = ''; 
               for(var j = 0; j < keySet.length; j++){ 
                   var idTag = keySet[j]; 
                   msg += idTag; 
                   if(idTag.indexOf("T") == 0){ 
                       /* text frame*/ 
                       if(onSafari){ 
                           /* text frame data is exposed in object format 
                            * where corresponding text data is exposed through 
                            * data key of text frame data object 
                            * */ 
                           var frameDataObject = md.getObject(idTag); 
                           msg += " : " + frameDataObject.data; 
                       } else { 
                           var buff = md.getByteArray(idTag); 
                           msg += " : " + hex2a(buff, 0, buff.length - 1); 
                       } 
                   } 
                   msg += " ; "; 
               } 
           } 
       } 
   } 
   ```

