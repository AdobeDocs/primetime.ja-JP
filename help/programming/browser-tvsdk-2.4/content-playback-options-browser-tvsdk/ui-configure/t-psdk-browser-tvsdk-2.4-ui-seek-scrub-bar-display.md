---
description: ブラウザー TVSDK では、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライドウィンドウ型のプレイリストまたはビデオオンデマンド (VOD) コンテンツにすることができます。
title: シークバーを使用する場合にシークを処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# シークバーを使用する場合にシークを処理{#handle-seek-when-using-the-seek-bar}

ブラウザー TVSDK では、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライドウィンドウ型のプレイリストまたはビデオオンデマンド (VOD) コンテンツにすることができます。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVR でのみ許可されます。

1. ブラウザー TVSDK がシークの有効な状態になるのを待ちます。

   有効な状態は、準備済み、完了、一時停止および再生です。 有効な状態にある場合、メディアリソースは正常に読み込まれたことを確認します。 プレーヤーがシーク可能な状態になっていない場合に、以下のメソッドを呼び出そうとすると、 `IllegalStateException`.

   例えば、Browser TVSDK がトリガーするまで待つことができます  `AdobePSDK.MediaPlayerStatusChangeEvent`  と `event.status` / `AdobePSDK.MediaPlayerStatus.PREPARED`.

1. リクエストされたシーク位置を `MediaPlayer.seek` メソッドをミリ秒単位のパラメーターとして使用します。

   これにより、再生ヘッドがストリーム内の別の位置に移動します。

   >[!TIP]
   >
   >要求されたシーク位置は、実際に計算された位置と一致しない可能性があります。

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. ブラウザー TVSDK が  `AdobePSDK.PSDKEventType.SEEK_END`  イベント内の調整後の位置を返すイベント `actualPosition` 属性：

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   シーク後の実際の開始位置が要求された位置と異なる場合があるので、これは重要です。 次のルールの一部が適用される場合があります。

   * シークやその他の再配置によって、広告の途中で終わるか、広告の時間をスキップすると、再生動作に影響します。
   * アセットのシーク可能な期間内にのみシークできます。 VOD の場合は、0 ～アセットの期間です。

1. 上記の例で作成されたシークバーについては、 `setPositionChangeListener()` ユーザーがスクラブしている時期を確認するには：

   ```js
   seekBar.setPositionChangeListener(function (pos) { 
                   var range = player.seekableRange; 
                   if (range) { 
                       var duration = range.duration; 
                       var time = duration * pos; // seek bar range is [0,1] 
                       player.seek(time); 
   
                       console.log("seek to " + time + " / " + duration); 
                   } 
   
               }); 
   ```

1. ユーザーのシークアクティビティの変更に対するイベントリスナーコールバックを設定します。

       シーク操作は非同期なので、Browser TVSDK は、シークに関連する次のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` を使用して、シークが開始されていることを示します。
   * `AdobePSDK.PSDKEventType.SEEK_END` をクリックして、シークが成功したことを示します。
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` を使用して、ユーザーが提供するシーク位置をメディアプレーヤーが再調整したことを示します。
