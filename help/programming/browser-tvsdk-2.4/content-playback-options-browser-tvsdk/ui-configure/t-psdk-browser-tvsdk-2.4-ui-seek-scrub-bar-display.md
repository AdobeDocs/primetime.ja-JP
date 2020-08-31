---
description: ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。
seo-description: ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。
seo-title: シークバーを使用する場合にシークを処理する
title: シークバーを使用する場合にシークを処理する
uuid: a7c74141-581f-40a3-9d28-ce56ba56773c
translation-type: tm+mt
source-git-commit: 1985694f99c548284aad6e6b4e070bece230bdf4
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# シークバーを使用する場合にシークを処理する{#handle-seek-when-using-the-seek-bar}

ブラウザーTVSDKでは、ストリーム内の特定の位置（時間）をシークできます。 ストリームは、スライディングウィンドウプレイリストまたはビデオオンデマンド(VOD)コンテンツにすることができます。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVRでのみ可能です。

1. ブラウザーTVSDKがシーク可能な状態になるのを待ちます。

   有効な状態は、PREPARED、COMPLETE、PAUSEDおよびPLAYINGです。 有効な状態にあると、メディアリソースは正常に読み込まれたことを確認できます。 プレイヤーがシーク可能な状態になっていない場合に、以下のメソッドを呼び出そうとすると、 `IllegalStateException`

   例えば、の値を使用してBrowser TVSDKがトリガーされるのを待つこ `AdobePSDK.MediaPlayerStatusChangeEvent` とがで `event.status` き `AdobePSDK.MediaPlayerStatus.PREPARED`ます。

1. 要求されたシーク位置をミリ秒単位のパラメーターとして `MediaPlayer.seek` メソッドに渡します。

   これにより、再生ヘッドがストリーム内の別の位置に移動します。

   >[!TIP]
   >
   >要求されたシーク位置は、計算された実際の位置と一致しない場合があります。

   ```js
   void seek(long position) throws IllegalStateException;
   ```

1. Browser TVSDKが `AdobePSDK.PSDKEventType.SEEK_END` イベントをトリガーするのを待ちます。これにより、調整された位置がイベントの `actualPosition` 属性に返されます。

   ```js
   player.addEventListener(AdobePSDK.PSDKEventType.SEEK_END, onSeekComplete); 
   onSeekComplete = function (event) {
       // event.actualPosition
   }
   ```

   シーク後の実際の開始位置が、要求された位置と異なる可能性があるので、これは重要です。 次のルールの一部が適用される場合があります。

   * シークやその他の位置変更が、広告の時間の途中で終了するか、広告をスキップすると、再生動作に影響します。
   * アセットのシーク可能な時間内でのみシークできます。 VODの場合、0 ～アセットの期間。

1. 上の例で作成したシークバーについて、でユーザーがスクラブしてい `setPositionChangeListener()` るタイミングをリッスンします。

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

1. イベントリスナーコールバックを設定して、ユーザーのシークアクティビティの変更を確認します。

       シーク操作は非同期的なので、Browser TVSDKは、シーク操作に関連する次のイベントをディスパッチします。
   
   * `AdobePSDK.PSDKEventType.SEEK_BEGIN` を設定します。
   * `AdobePSDK.PSDKEventType.SEEK_END` を呼び出します。
   * `AdobePSDK.PSDKEventType.SEEK_POSITION_ADJUSTED` メディアプレイヤーがユーザーが指定したシーク位置を再調整したことを示します。

