---
description: MediaPlayer インスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは状態間の一連の遷移を完了します。
title: MediaPlayer オブジェクトのライフサイクル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MediaPlayer オブジェクトのライフサイクル{#mediaplayer-object-lifecycle}

MediaPlayer インスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは状態間の一連の遷移を完了します。

一部の操作は、プレーヤーが特定の状態にある場合にのみ許可されます。 例： `play` in `IDLE` は許可されていません。 このステータスは、プレーヤーが `PREPARED` 状態。

状態を操作するには：

* 現在の `MediaPlayer` ～に対して `MediaPlayer.getStatus`.

  ```java
  PlayerState getStatus() throws IllegalStateException;
  ```

* 状態のリストは、 `MediaPlayer.PlayerState`.

のライフサイクルの状態遷移図 `MediaPlayer` インスタンス：
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

その他の詳細を次の表に示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> MediaPlayer.PlayerState </th> 
   <th colname="col2" class="entry"> 発生するタイミング </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> アイドル </span> </td> 
   <td colname="col2"> <p>アプリケーションが <span class="codeph"> DefaultMediaPlayer.create </span>. 新しく作成されたプレーヤーは、メディアプレーヤーアイテムの指定を待っています。 これは、メディアプレーヤーの初期状態です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化中 </span> </td> 
   <td colname="col2"> <p>アプリケーションの名前： <span class="codeph"> MediaPlayer.replaceCurrentItem </span>、メディアプレーヤーが読み込まれている状態。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化済み </span> </td> 
   <td colname="col2"> <p>TVSDK は、メディアプレーヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 準備中 </span> </td> 
   <td colname="col2"> <p>アプリケーションの名前： <span class="codeph"> MediaPlayer.prepareToPlay </span>. メディアプレーヤーは、メディアプレーヤーアイテムと関連するリソースを読み込んでいます。 </p> <p>ヒント：メインメディアのバッファリングが発生する場合があります。 </p> <p>TVSDK は、メディアストリームを準備中で、広告解決と広告挿入を実行しようとしています（有効な場合）。 </p> <p>ヒント：開始時間をゼロ以外の値に設定するには、を呼び出します。 <span class="codeph"> prepareToPlay(startTime) </span> 時間をミリ秒単位で指定します。 </p> </td> 
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
   <td colname="col1"> <span class="codeph"> 中断 </span> </td> 
   <td colname="col2"> <p>プレーヤーの再生中または一時停止中に、アプリケーションが再生から切り離されたり、デバイスをシャットダウンしたり、アプリケーションを切り替えたりした場合。 メディアプレーヤーが中断され、リソースがリリースされました。 続行するには、メディアプレーヤーを復元します。 </p> </td> 
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
>状態を使用して、プロセスに関するフィードバック（次の状態の変更を待つ間、スピナーなど）を提供したり、次のメソッドを呼び出す前に適切な状態を待つなど、メディアを再生する際に次の手順を実行したりできます。

例：

```java
@Override 
public void onStateChanged(MediaPlayer.PlayerState state,  
                           MediaPlayerNotification notification) { 
   switch (state) { 
      // It is recommended that you call prepareToPlay() after receiving  
      // the INITIALIZED state. 
      case INITIALIZED: 
         _mediaPlayer.prepareToPlay(); 
         break; 
      case PREPARING: 
         showBufferingSpinner(); 
         break; 
      case PREPARED: 
         hideBufferingSpinner(); 
      ..... 
    } 
}
```
