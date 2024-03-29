---
description: TVSDK は、ビデオオンデマンド (VOD) とライブストリームの両方で、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています。
title: シークスクラブバーを現在の再生位置で表示
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# シークスクラブバーを現在の再生位置で表示{#display-a-seek-scrub-bar-with-the-current-playback-position}

TVSDK は、ビデオオンデマンド (VOD) とライブストリームの両方で、ストリームがスライドウィンドウプレイリストである特定の位置（時間）へのシークをサポートしています。

>[!IMPORTANT]
>
>ライブストリームでのシークは、DVR でのみ許可されます。

1. シークのコールバックを設定します。

       シークは非同期なので、 TVSDK は以下のシーク関連イベントをディスパッチします。
   
   * `SeekEvent.SEEK_BEGIN`  — シーク開始。
   * `SeekEvent.SEEK_END`  — シークに成功しました。
   * `SeekEvent.SEEK_POSITION_ADJUSTED`  — ユーザーが指定したシーク位置を再調整しました。

1. プレーヤーがシークの有効なステータスになるのを待ちます。

   有効な状態は、準備済み、完了、一時停止および再生です。

1. 適切なイベントをリッスンして、ユーザーがスクラブしているタイミングを確認します。
1. 要求されたシーク位置（ミリ秒）を `MediaPlayer.seek` メソッド。

   ```
   function seek(position:Number):void;
   ```

   アセットのシーク可能な期間内にのみシークできます。 ビデオオンデマンドの場合、期間は 0 ～アセットの期間です。

   >[!TIP]
   >
   >これにより、再生ヘッドがストリーム内の新しい位置に移動しますが、最終的に計算された位置は、指定されたシーク位置とは異なる場合があります。

1. TVSDK が `SeekEvent.SEEK_END` イベント。
1. event.actualPosition を使用して、最終的に調整された再生位置を取得します。

       シーク後の実際の開始位置は、リクエストされた位置と異なる場合があるので、これは重要です。 次のような様々なルールが適用されます。
   
   * シークやその他の再配置が広告の途中で終了したり、広告の時間をスキップしたりすると、再生動作に影響します。
   * セグメント境界の近くをシークした場合、シーク位置はセグメントの先頭に調整されます。

1. シークスクラブバーを表示する際には、位置情報を使用します。
