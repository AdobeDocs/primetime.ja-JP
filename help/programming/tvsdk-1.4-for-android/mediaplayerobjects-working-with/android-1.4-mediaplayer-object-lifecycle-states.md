---
description: MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは状態間の一連の遷移を完了します。
seo-description: MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは状態間の一連の遷移を完了します。
seo-title: MediaPlayerオブジェクトのライフサイクル
title: MediaPlayerオブジェクトのライフサイクル
uuid: 6670a30c-7053-4754-bc36-6bb8590c001d
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# MediaPlayerオブジェクトのライフサイクル{#mediaplayer-object-lifecycle}

MediaPlayerインスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスは状態間の一連の遷移を完了します。

一部の操作は、プレイヤーが特定の状態の場合にのみ許可されます。 例えば、での呼び出し `play` は許可 `IDLE` されません。 このステータスは、プレイヤーが状態に達した後でのみ呼び出すことがで `PREPARED` きます。

ステートを操作するには：

* オブジェクトの現在の状態を取得するには、を使 `MediaPlayer` 用しま `MediaPlayer.getStatus`す。

   ```java
   PlayerState getStatus() throws IllegalStateException;
   ```

* 状態のリストは、で定義されます `MediaPlayer.PlayerState`。

インスタンスのライフサイクルの状態遷移図 `MediaPlayer` :
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-android_1.2_web.png)

次の表に、その他の詳細を示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> MediaPlayer.PlayerState </th> 
   <th colname="col2" class="entry"> 発生するのは </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <span class="codeph"> IDLE </span> </td> 
   <td colname="col2"> <p>アプリケーションがDefaultMediaPlayer.createを呼び出して新しいメディアプレ <span class="codeph"> イヤーを要求しまし </span>た。 新しく作成されたプレイヤーは、メディアプレイヤー項目の指定を待っています。 これは、メディアプレイヤーの初期状態です。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 初期化中 </span> </td> 
   <td colname="col2"> <p>アプリケーション <span class="codeph"> MediaPlayer.replaceCurrentItemが呼び出され、 </span>メディアプレイヤーが読み込まれています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> INITIALIZED </span> </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤー項目を正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 準備中 </span> </td> 
   <td colname="col2"> <p>アプリケーションの <span class="codeph"> 名前はMediaPlayer.prepareToPlayで </span>す。 メディアプレイヤーは、メディアプレイヤー項目と関連リソースを読み込んでいます。 </p> <p>ヒント： メインメディアのバッファリングが発生する場合があります。 </p> <p>TVSDKは、メディアストリームを準備し、広告解決と広告挿入を実行しようとしています（有効な場合）。 </p> <p>ヒント： 開始時間をゼロ以外の値に設定するには、 <span class="codeph"> prepareToPlay(startTime)を呼び出し、時 </span> 間をミリ秒で指定します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PREPARED </span> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入されたか、広告手順が失敗した。 バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 再生中 </span> </td> 
   <td colname="col2"> <p>アプリケーションが <span class="codeph"> playを呼び </span>出したので、TVSDKはビデオの再生を試みています。 ビデオが実際に再生される前に、バッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> PAUSED </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこの状態とPLAYINGの間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 休止 </span> </td> 
   <td colname="col2"> <p>アプリケーションが再生から離れたり、デバイスをシャットダウンしたり、プレイヤーの再生中または一時停止中にアプリケーションを切り替えたりしました。 メディアプレイヤーは停止され、リソースが解放されました。 続行するには、メディアプレイヤーを復元します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> 完了 </span> </td> 
   <td colname="col2"> <p>プレイヤーがストリームの最後に到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> RELEASED </span> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連するリソースもすべて解放しました。 このインスタンスは使用できなくなりました </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> エラー </span> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える可能性があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>この状態を使用して、プロセスに対するフィードバック（例えば、次の状態の変更を待つ間のスピナー）を提供したり、次のメソッドを呼び出す前に適切な状態を待つなど、メディアの再生時に次の手順を実行したりできます。

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

