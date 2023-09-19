---
description: MediaPlayer インスタンスが作成された瞬間から終了する瞬間まで、このインスタンスはある状態から次の状態に遷移します。
title: MediaPlayer オブジェクトのライフサイクルと状態
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# MediaPlayer オブジェクトのライフサイクルと状態{#life-cycle-and-states-of-the-mediaplayer-object}

MediaPlayer インスタンスが作成された瞬間から終了する瞬間まで、このインスタンスはある状態から次の状態に遷移します。

次に、考えられる状態を示します。

* **アイドル**: `MediaPlayerStatus.IDLE`

* **初期化中**: `MediaPlayerStatus.INITIALIZING`

* **初期化済み**: `MediaPlayerStatus.INITIALIZED`

* **準備中**: `MediaPlayerStatus.PREPARING`

* **準備済み**: `MediaPlayerStatus.PREPARED`

* **再生中**: `MediaPlayerStatus.PLAYING`

* **一時停止**: `MediaPlayerStatus.PAUSED`

* **シーク**: `MediaPlayerStatus.SEEKING`

* **完了**: `MediaPlayerStatus.COMPLETE`

* **エラー**: `MediaPlayerStatus.ERROR`

* **リリース済み**: `MediaPlayerStatus.RELEASED`

状態の完全なリストは、 `MediaPlayerStatus`.

一部の操作はプレーヤーが特定の状態にある間にのみ許可されるので、プレーヤーの状態を把握することは役に立ちます。 例： `play` IDLE 状態の間は呼び出せません。 PREPARED 状態に達した後で呼び出す必要があります。 ERROR 状態は、次に何が起こるかを変更します。

メディアリソースが読み込まれて再生されると、プレーヤーは次のように切り替わります。

1. 初期状態は IDLE です。
1. アプリケーションの呼び出し `MediaPlayer.replaceCurrentResource`：プレーヤーを INITIALIZING 状態に移行させます。
1. ブラウザー TVSDK がリソースを正常に読み込むと、状態は INITIALIZED に変わります。
1. アプリケーションの呼び出し `MediaPlayer.prepareToPlay`を呼び出し、状態が PREPARING に変わります。
1. ブラウザー TVSDK は、メディアストリームを準備し、広告の解決と広告の挿入を開始します（有効な場合）。

   この手順が完了すると、広告がタイムラインに挿入されるか、広告手順が失敗し、プレーヤーの状態が PREPARED に変わります。
1. アプリケーションがメディアを再生および一時停止すると、状態が PLAYING と PAUSED の間で移動します。

   >[!TIP]
   >
   >再生中または一時停止中に、再生から離れたり、デバイスをシャットダウンしたり、アプリケーションを切り替えたりすると、状態が「中断」に変わり、リソースが解放されます。 続行するには、メディアプレーヤーを復元します。

1. プレーヤーがストリームの終わりに到達すると、状態は COMPLETE になります。
1. アプリケーションがメディアプレーヤーを解放すると、状態は RELEASED に変わります。
1. プロセス中にエラーが発生した場合、状態は ERROR に変わります。

MediaPlayer インスタンスのライフサイクルを図に示します。

<!--<a id="fig_DD3DAE7507C549C8A4720A26DFCFFCCB"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

状態を使用して、プロセス上のユーザーにフィードバックを提供したり（例えば、次の状態の変更を待機している間は、スピナーを表示）、次のメソッドを呼び出す前に適切な状態を待つなど、メディアを再生する際に次の手順を実行したりできます。

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
