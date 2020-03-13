---
description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 ブラウザーTVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
seo-description: ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 ブラウザーTVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
seo-title: ID3タグ
title: ID3タグ
uuid: a47cd0cc-b11d-47df-b1fb-56918896ef4c
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ID3タグ{#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 ブラウザーTVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

基になるHLSストリームで新しいID3メタデータが見つかると、Browser TVSDKはイベントをトリガー `AdobePSDK.TimedMetadataEvent` します。

ID3の `TimedMetadata` オブジェクトには、次のプロパティがあります。

<table id="table_6C61886187FB44B4B9821E4B00200018"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> プロパティ名 </th> 
   <th colname="col2" class="entry"> 詳細 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> type </span> </p> </td> 
   <td colname="col2"> <p>TimedMetadataオブジェクト <span class="codeph"> のタ </span> イプ。 </p> <p>ID3メタデータの場合、値 <span class="codeph"> はAdobePSDK.TimedMetadataType.ID3です </span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> time </span> </p> </td> 
   <td colname="col2"> <p> この時間指定メタデータが検出されたプレイヤーの時間。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id </span> </p> </td> 
   <td colname="col2"> <p>TimedMetadataオブジェ <span class="codeph"> クトの </span> ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> name </span> </p> </td> 
   <td colname="col2"> <p>TimedMetadataオブジェ <span class="codeph"> クトの </span> 名前。 ID3メタデータの場合、値は「ID3」です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> コンテンツ </span> </p> </td> 
   <td colname="col2"> <p>時間指定メタデータのコンテンツ。 ID3タグの場合、この値はシリアライズされたバイト配列を表します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> メタデータ </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> TimedMetadataが処理 </span> した情報。これは、ID3フレームが <span class="codeph"> 保存されるAdobePSDK.Metadata </span> のインスタンスです。 </p> <p> <p>注意： Safariビデオタ <span class="codeph"> グ </span> の場合、ID3タグの特定のフレームデータは、AdobePSDK.Metadataオブジェクトを通じてオブジェクトの形式で公開され、他のブラウザーの場合、ID3タグのフレームデータは、 <span class="codeph"> AdobePSDK.Metadataオブジェクトを通じてバイト配列の形式で公開され </span><span class="codeph"></span> ます。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

に保存される様々なID3タグは、次の2 `TimedMetadata` つの方法でアプリケーションから取得できます。

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

* のプロパ `MediaPlayerItem`ティを使 `timedMetadata` 用する。

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

