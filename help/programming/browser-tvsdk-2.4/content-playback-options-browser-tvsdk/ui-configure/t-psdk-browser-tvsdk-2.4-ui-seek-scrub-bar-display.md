---
description: ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。
seo-description: ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。
seo-title: シークバーを使用する場合にシークを処理する
title: シークバーを使用する場合にシークを処理する
uuid: a7c74141-581f-40a3-9d28-ce56ba56773c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# シークバーを使用する場合にシークを処理する{#handle-seek-when-using-the-seek-bar}

ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVRでのみ許可されます。

1. ブラウザーTVSDKがシーク可能な状態になるのを待ちます。

   有効な状態は、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。 有効な状態になっていると、メディアリソースが正常に読み込まれたことを確認できます。 プレイヤーがシーク可能な状態でない場合、次のメソッドを呼び出そうとすると、 `IllegalStateException`

   例えば、ブラウザーTVSDKが、の `AdobePSDK.MediaPlayerStatusChangeEvent``event.status``AdobePSDK.MediaPlayerStatus.PREPARED`

1. 要求されたシーク位置をミリ秒単位のパ `MediaPlayer.seek` ラメーターとしてメソッドに渡します。

   これにより、再生ヘッドがストリーム内の別の位置に移動します。

   >[!TIP]
   >
   >要求されたシーク位置は、実際に計算された位置と一致しない可能性があります。

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. ブラウザーTVSDKがイベントをトリガ `AdobePSDK.PSDKEventType.SEEK_END` ーするまで待ちます。このイベントは、調整された位置をイベントの属性に返 `actualPosition` します。

       &quot;js
    player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete);
      onSeekComplete = function (event) {
 // event.actualPosition     &quot;
 &quot;シーク後の実際の開始位置は要求された位置と異なるので、     
    
    
    この開始位置は重要です。 次のルールの一部が適用されます。
   
   * シークやその他の再配置が広告の時間の途中で終了するか、広告の時間をスキップすると、再生動作に影響します。
   * シークできるのは、アセットのシーク可能な時間内だけです。 VODの場合、0からアセットの期間までの値。

1. 上の例で作成したシークバーについて、ユーザーがスクラブし `setPositionChangeListener()` ているタイミングをリッスンします。

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

1. イベントリスナーコールバックを設定し、ユーザーのシークアクティビティの変更を確認します。

       シーク操作は非同期なので、Browser TVSDKはシークに関連する次のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` を使用して、シークが開始されていることを示します。
   * `AdobePSDK.PSDKEventType.SEEK_END` 検索が成功したことを示す
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` メディアプレイヤーが、ユーザーが指定したシーク位置を再調整したことを示します。

