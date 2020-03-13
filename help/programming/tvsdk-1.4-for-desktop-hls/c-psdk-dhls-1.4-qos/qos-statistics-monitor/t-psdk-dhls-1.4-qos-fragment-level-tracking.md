---
description: フラグメントやトラックなど、LoadInformationクラスからダウンロードされたリソースに関するサービス品質(QoS)情報を読み取ることができます。
seo-description: フラグメントやトラックなど、LoadInformationクラスからダウンロードされたリソースに関するサービス品質(QoS)情報を読み取ることができます。
seo-title: 読み込み情報を使用してフラグメントレベルで追跡
title: 読み込み情報を使用してフラグメントレベルで追跡
uuid: 41fb2b90-3531-4cc5-bf9b-01ccae04d2fd
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 読み込み情報を使用してフラグメントレベルで追跡{#track-at-the-fragment-level-using-load-information}

フラグメントやトラックなど、LoadInformationクラスからダウンロードされたリソースに関するサービス品質(QoS)情報を読み取ることができます。

1. コールバックイベ `onLoadInformationAvailable` ントリスナーを実装します。

   ```
   private function onLoadInformationAvailable(event:LoadInformationEvent):void { 
       var loadInformation:LoadInformation = event.loadInformation; 
       // process the load information here     
   }
   ```

1. フラグメントがダウンロードされるたびにTVSDKが呼び出すイベントリスナーを登録します。

   ```
   player.addEventListener(LoadInformationEvent.LOAD_INFORMATION_AVAILABLE,  
                                    onLoadInformationAvailable);
   ```

1. コールバックに渡されるから、関 `LoadInformation` 心のあるデータを読み取ります。

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
      <td colname="col2"> <p>ダウンロードの時間（ミリ秒）。 </p> <p>TVSDKは、クライアントがサーバーに接続するのに要した時間と、フラグメント全体のダウンロードに要した時間を区別しません。 例えば、10 MBのセグメントのダウンロードに8秒かかる場合、TVSDKはこの情報を提供しますが、最初のバイトまで4秒かかり、フラグメント全体のダウンロードに4秒かかったとは通知しません。 </p> </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> mediaDuration </span> </td> 
      <td colname="col1"> <p>数値 </p> </td> 
      <td colname="col2"> ダウンロードされたフラグメントのメディア時間（ミリ秒）。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> size </span> </td> 
      <td colname="col1"> <p>数値 </p> </td> 
      <td colname="col2"> ダウンロードされたリソースのサイズ（バイト単位）。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackIndex </span> </td> 
      <td colname="col1"> <p>int </p> </td> 
      <td colname="col2"> 対応するトラックのインデックス（わかっている場合）。それ以外の場合は、0。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackName </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> 対応するトラックの名前（わかっている場合）。それ以外の場合はnull。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> trackType </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> 対応するトラックのタイプ（わかっている場合）。それ以外の場合はnull。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> type </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> TVSDKがダウンロードした内容。 次のいずれかです。 
      <ul id="ul_FA02F42D109344F4866073908CA4E835"> 
      <li id="li_0E2D3EBCAB58477FB5EA526C54FACFFB">MANIFEST — プレイリスト/マニフェスト </li> 
      <li id="li_D7894C2F0CB64C909C6398288EA5683A">FRAGMENT — フラグメント </li> 
      <li id="li_4D4FEDB7704C411B80891B5028B0C20E">TRACK — 特定のトラックに関連付けられたフラグメント </li> 
      </ul> リソースのタイプを検出できない場合があります。 この場合、FILEが返されます。 </td> 
   </tr> 
   <tr> 
      <td colname="col01"> <span class="codeph"> url </span> </td> 
      <td colname="col1"> <p>文字列 </p> </td> 
      <td colname="col2"> ダウンロードされたリソースを指すURL。 </td> 
   </tr> 
   </tbody> 
   </table>
