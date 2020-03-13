---
description: MediaPlayerインスタンスが作成された瞬間から終了する瞬間まで、このインスタンスはある状態から次の状態に移行します。
seo-description: MediaPlayerインスタンスが作成された瞬間から終了する瞬間まで、このインスタンスはある状態から次の状態に移行します。
seo-title: MediaPlayerオブジェクトのライフサイクルと状態
title: MediaPlayerオブジェクトのライフサイクルと状態
uuid: fe76ea80-aaa8-43bc-9b81-85e0551f70dd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# MediaPlayerオブジェクトのライフサイクルと状態{#life-cycle-and-states-of-the-mediaplayer-object}

MediaPlayerインスタンスが作成された瞬間から終了する瞬間まで、このインスタンスはある状態から次の状態に移行します。

次に、考えられる状態を示します。

* **IDLE**: `MediaPlayerStatus.IDLE`

* **初期化**: `MediaPlayerStatus.INITIALIZING`

* **INITIALIZED**: `MediaPlayerStatus.INITIALIZED`

* **準備中**: `MediaPlayerStatus.PREPARING`

* **PREPARED**: `MediaPlayerStatus.PREPARED`

* **再生**: `MediaPlayerStatus.PLAYING`

* **PAUSED**: `MediaPlayerStatus.PAUSED`

* **シーク**: `MediaPlayerStatus.SEEKING`

* **完了**: `MediaPlayerStatus.COMPLETE`

* **エラー**: `MediaPlayerStatus.ERROR`

* **RELEASED**: `MediaPlayerStatus.RELEASED`

状態の完全なリストは、で定義されていま `MediaPlayerStatus`す。

一部の操作は、プレイヤーが特定の状態にある間のみ許可されるので、プレイヤーの状態を把握することは役に立ちます。 例えば、IDLE状態 `play` の間は呼び出すことはできません。 PREPARED状態に達した後に呼び出す必要があります。 ERROR状態は、次に何が起きるかも変更します。

メディアリソースの読み込みと再生が進むと、プレイヤーは次のように移動します。

1. 初期状態はIDLEです。
1. アプリケーションが呼 `MediaPlayer.replaceCurrentResource`び出しを行い、プレイヤーがINITIALIZING状態に移行します。
1. ブラウザーTVSDKがリソースを正常に読み込むと、状態はINITIALIZEDに変更されます。
1. アプリケーションが `MediaPlayer.prepareToPlay`呼び出され、状態がPREPARINGに変わります。
1. ブラウザーTVSDKは、メディアストリームを準備し、広告解決と広告挿入を開始します（有効な場合）。

   この手順が完了すると、広告がタイムラインに挿入されるか、広告手順が失敗し、プレイヤーの状態がPREPAREDに変わります。
1. アプリケーションがメディアを再生および一時停止すると、状態がPLAYINGとPAUSEDの間で切り替わります。

   >[!TIP]
   >
   >再生中または一時停止中、再生から移動したり、デバイスをシャットダウンしたり、アプリケーションを切り替えたりすると、状態が「休止」に変わり、リソースが解放されます。 続行するには、メディアプレイヤーを復元します。

1. プレイヤーがストリームの終わりに到達すると、状態はCOMPLETEになります。
1. アプリケーションがメディアプレイヤーを解放すると、状態がRELEASEDに変わります。
1. プロセス中にエラーが発生した場合、状態はERRORに変更されます。

以下に、MediaPlayerインスタンスのライフサイクルを示します。

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

この状態を使用して、プロセス上のユーザーにフィードバック（例えば、次の状態の変更を待つ間のスピナー）を提供したり、次のメソッドを呼び出す前に適切な状態を待つなど、メディアの再生時に次の手順を実行したりできます。

例：

```js
function onStateChanged(state) { 
    switch(state) { 
        // It is recommended that you call prepareToPlay()  
        // after receiving the INITIALIZED state             
        case AdobePSDK.MediaPlayerStatus.INITIALIZED: 
            mediaPlayer.prepareToPlay(); 
            break; 
    } 
} 
```

