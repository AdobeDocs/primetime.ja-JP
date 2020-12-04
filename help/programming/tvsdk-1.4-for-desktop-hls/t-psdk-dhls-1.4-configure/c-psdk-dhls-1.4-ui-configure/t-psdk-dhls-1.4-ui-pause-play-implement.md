---
description: TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。
seo-description: TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。
seo-title: ビデオの再生と一時停止
title: ビデオの再生と一時停止
uuid: 04b3b23f-5ef1-4cc4-a22f-f6ffa9cefce5
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# ビデオの再生と一時停止{#play-and-pause-a-video}

TVSDKの動作を追加して、一時停止ボタンと再生ボタンを追加できます。

1. 以下を実行する一時停止/再生ボタンを作成します。
   1. プレイヤーがPREPAREDステータスになるまで待ちます。
   1. 開始を再生するには、TVSDKのplayメソッドを呼び出します。

      ```
      function play():void;
      ```

   1. 再生を一時停止するには、TVSDKのpauseメソッドを呼び出します。

      ```
      function pause():void;
      ```

1. `MediaPlayerStatusChangeEvent.STATUS_CHANGED`イベントのコールバックを使用して、エラーを確認したり、他の適切な操作を行ったりします。

   TVSDKは、pauseメソッドまたはplayメソッドが呼び出されると、このコールバックを呼び出します。 TVSDKは、PAUSEDやPLAYINGなどの新しいステータスに関する情報を、コールバックで渡します。
