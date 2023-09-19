---
description: ID3 タグは、ファイルのタイトルやアーティスト名など、オーディオまたはビデオファイルに関する情報を提供します。 ブラウザー TVSDK は、HLS ストリームのトランスポートストリーム (TS) セグメントレベルで ID3 タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。
title: ID3 タグ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# ID3 タグ{#id-tags}

ID3 タグは、ファイルのタイトルやアーティスト名など、オーディオまたはビデオファイルに関する情報を提供します。 ブラウザー TVSDK は、HLS ストリームのトランスポートストリーム (TS) セグメントレベルで ID3 タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

基になる HLS ストリームで新しい ID3 メタデータが見つかると、Browser TVSDK は、 `AdobePSDK.TimedMetadataEvent` イベント。

The `TimedMetadata` ID3 のオブジェクトには次のプロパティがあります。

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
   <td colname="col2"> <p>のタイプ <span class="codeph"> TimedMetadata </span> オブジェクト。 </p> <p>ID3 メタデータの場合、値は <span class="codeph"> AdobePSDK.TimedMetadataType.ID3 </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> 時間 </span> </p> </td> 
   <td colname="col2"> <p> この時間指定メタデータが検出されたプレーヤーの時間。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> id </span> </p> </td> 
   <td colname="col2"> <p>の ID <span class="codeph"> TimedMetadata </span> オブジェクト。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> 名前 </span> </p> </td> 
   <td colname="col2"> <p>名前： <span class="codeph"> TimedMetadata </span> オブジェクト。 ID3 メタデータの場合、値は「ID3」です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> コンテンツ </span> </p> </td> 
   <td colname="col2"> <p>時間指定メタデータコンテンツ。 ID3 タグの場合、この値はシリアル化されたバイト配列を表します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> メタデータ </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> TimedMetadata </span> 処理済みの情報 ( <span class="codeph"> AdobePSDK.Metadata </span> ここで、ID3 フレームが保存されます。 </p> <p> <p>注意：Safari の場合 <span class="codeph"> ビデオ </span> タグ、ID3 タグの特定のフレームデータは、 <span class="codeph"> AdobePSDK.Metadata </span> オブジェクトを使用するのに対して、他のブラウザーでは、ID3 タグのフレームデータは、 <span class="codeph"> AdobePSDK.Metadata </span> オブジェクト。 </p> </p> </td> 
  </tr> 
 </tbody> 
</table>

&#x200B;

に保存される様々な ID3 タグ `TimedMetadata` は、次の 2 つの方法でアプリケーションで取得できます。

* AdobePSDK.PSDKEventType.TIMED_METADATA_AVAILABLE イベントリスナー内。

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

* の使用 `MediaPlayerItem`&#39;s `timedMetadata` プロパティ。

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
