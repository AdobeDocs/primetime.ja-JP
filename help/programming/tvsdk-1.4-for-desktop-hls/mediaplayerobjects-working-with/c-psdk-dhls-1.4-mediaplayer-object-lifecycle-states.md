---
description: MediaPlayer インスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスはステータス間の一連の遷移を完了します。
title: MediaPlayer オブジェクトのライフサイクル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# MediaPlayer オブジェクトのライフサイクル{#mediaplayer-object-lifecycle}

MediaPlayer インスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスはステータス間の一連の遷移を完了します。

一部の操作は、プレーヤーが特定の状態にある場合にのみ許可されます。 例： `play` IDLE では許可されていません。 このステータスは、プレーヤーが PREPARED 状態に達した後でのみ呼び出すことができます。

ステータスを処理するには：

* 現在の `MediaPlayer` オブジェクトを `MediaPlayer.status` プロパティ。

  ```
  function get status():String;
  ```

* ステータスのリストは、 `MediaPlayer.PlayerStatus`.

のライフサイクルの状態遷移図 `MediaPlayer` インスタンス：
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-flash-1_2_web.png)

その他の詳細を次の表に示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <span class="codeph"> MediaPlayerStatus </span> </th> 
   <th colname="col2" class="entry"> 発生するタイミング </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> アイドル </span> </td> 
   <td colname="col2"> <p> アプリケーションが、 <span class="codeph"> MediaPlayer </span>. 新しく作成されたプレーヤーは、メディアプレーヤーアイテムの指定を待っています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化中 </span> </td> 
   <td colname="col2"> <p>アプリケーションの名前： <span class="codeph"> MediaPlayer.replaceCurrentResource </span>、メディアプレーヤーが読み込まれている状態。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化済み </span> </td> 
   <td colname="col2"> <p>TVSDK は、メディアプレーヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 準備中 </span> </td> 
   <td colname="col2"> <p>アプリケーションの名前： <span class="codeph"> MediaPlayer.prepareToPlay </span>. メディアプレーヤーは、メディアプレーヤーアイテムと関連するリソースを読み込んでいます。 </p> <p>ヒント：メインメディアのバッファリングが発生する場合があります。 </p> <p>TVSDK は、メディアストリームを準備中で、広告解決と広告挿入を実行しようとしています（有効な場合）。 </p> <p>ヒント：開始時間をゼロ以外の値に設定するには、を呼び出します。 <span class="codeph"> prepareToPlay(startTime) </span> ミリ秒単位で </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 準備済み </span> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入された、または広告手順が失敗した。 バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 再生中 </span> </td> 
   <td colname="col2"> <p>アプリケーションがを呼び出しました <span class="codeph"> play </span>そのため、 TVSDK はビデオを再生しようとしています。 ビデオが実際に再生される前にバッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 一時停止 </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレーヤーはこの状態と PLAYING の間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> シーク </span> </td> 
   <td colname="col2"> <p>一時停止中または再生中に、メディアプレーヤーが正しい位置をシークしています。 シークが開始または終了したタイミングを判断するには、 <span class="codeph"> SeekEvent.SEEK_BEGIN </span> および <span class="codeph"> SeekEvent.SEEK_END </span> イベント。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 完了 </span> </td> 
   <td colname="col2"> <p>プレーヤーがストリームの終わりに到達し、再生が停止した。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> リリース済み </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレーヤーをリリースし、関連するリソースもリリースしました。 このインスタンスは使用できなくなりました </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> エラー </span> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える場合があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに関するフィードバックを提供したり（例えば、次のステータスの変更を待つ間は、スピナーを表示）、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアを再生する際に次の手順を実行できます。
