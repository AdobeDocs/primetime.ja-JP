---
description: MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは一連のステータス間のトランジションを完了します。
seo-description: MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは一連のステータス間のトランジションを完了します。
seo-title: MediaPlayerオブジェクトのライフサイクル
title: MediaPlayerオブジェクトのライフサイクル
uuid: 1452ae3a-7ce9-439e-951c-9d3db63b1d20
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# MediaPlayerオブジェクトのライフサイクル{#mediaplayer-object-lifecycle}

MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは一連のステータス間のトランジションを完了します。

一部の操作は、プレイヤーが特定の状態にある場合にのみ許可されます。 例えば、IDLEで`play`を呼び出すことはできません。 このステータスは、プレイヤーがPREPARED状態に達した後でのみ呼び出すことができます。

ステータスを使用するには：

* `MediaPlayer.status`プロパティを使用して、`MediaPlayer`オブジェクトの現在の状態を取得できます。

   ```
   function get status():String;
   ```

* ステータスのリストは`MediaPlayer.PlayerStatus`に定義されています。

`MediaPlayer`インスタンスのライフサイクルの状態トランジション図：
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-flash-1_2_web.png)

次の表に、その他の詳細を示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> <span class="codeph"> MediaPlayerStatus  </span> </th> 
   <th colname="col2" class="entry"> 発生するのは </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE  </span> </td> 
   <td colname="col2"> <p> アプリケーションが、<span class="codeph"> MediaPlayer </span>をインスタンス化して、新しいメディアプレイヤーを要求しました。 新しく作成されたプレイヤーは、ユーザーがメディアプレイヤーアイテムを指定するのを待っています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化中  </span> </td> 
   <td colname="col2"> <p>アプリケーション名が<span class="codeph"> MediaPlayer.replaceCurrentResource </span>で、メディアプレイヤーが読み込まれています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALIZED  </span> </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 準備中  </span> </td> 
   <td colname="col2"> <p>アプリケーションの名前は<span class="codeph"> MediaPlayer.prepareToPlay </span>です。 メディアプレイヤーは、メディアプレイヤーアイテムと関連付けられたリソースを読み込んでいます。 </p> <p>ヒント： メインメディアのバッファリングが発生する場合があります。 </p> <p>TVSDKは、メディアストリームを準備中で、広告解決と広告挿入を実行しようとしています（有効な場合）。 </p> <p>ヒント： 開始時間をゼロ以外の値に設定するには、<span class="codeph"> prepareToPlay(startTime) </span>を呼び出し、時間をミリ秒単位で指定します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PREPARED  </span> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入されているか、広告手順が失敗しています。 バッファリングまたは再生が開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 再生中  </span> </td> 
   <td colname="col2"> <p>アプリケーションが<span class="codeph"> play </span>を呼び出したので、TVSDKはビデオの再生を試みています。 ビデオが実際に再生される前に、バッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PAUSED  </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこの状態とPLAYINGの間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> シーク  </span> </td> 
   <td colname="col2"> <p>一時停止中または再生中に、メディアプレイヤーが正しい位置をシークしています。 シークの開始と終了を判断するには、<span class="codeph"> SeekEvent.SEEK_BEGIN </span>および<span class="codeph"> SeekEvent.SEEK_END </span>イベントをリッスンします。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 完了  </span> </td> 
   <td colname="col2"> <p>プレイヤーがストリームの終わりに到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RELEASED  </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連付けられているリソースもすべて解放します。 このインスタンスは使用できなくなります </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> ERROR  </span> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響する可能性があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに対するフィードバック（例えば、次のステータス変更を待つ間のスピナー）を提供したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアの再生時に次の手順を実行したりできます。

