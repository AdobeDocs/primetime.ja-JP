---
description: PTMediaPlayer オブジェクトは、メディアプレーヤーを表します。 PTMediaPlayerItem は、プレーヤー上のオーディオまたはビデオを表します。
title: MediaPlayer オブジェクトの操作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MediaPlayer オブジェクトの操作 {#work-with-mediaplayer-objects}

PTMediaPlayer オブジェクトは、メディアプレーヤーを表します。 PTMediaPlayerItem は、プレーヤー上のオーディオまたはビデオを表します。

## MediaPlayerItem クラスについて {#section_B6F36C0462644F5C932C8AA2F6827071}

メディアリソースが正常に読み込まれた後、 TVSDK は `PTMediaPlayerItem` クラスを使用して、そのリソースへのアクセスを提供します。

The `PTMediaPlayer` メディアリソースを解決し、関連するマニフェストファイルを読み込んで、マニフェストを解析します。 これは、リソースの読み込みプロセスの非同期部分です。 The `PTMediaPlayerItem` インスタンスは、リソースが解決された後に生成され、このインスタンスはメディアリソースの解決されたバージョンです。 TVSDK は、新しく作成された `PTMediaPlayerItem` インスタンス経由で `PTMediaPlayer.currentItem`.

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレーヤーアイテムにアクセスする必要があります。

## MediaPlayer オブジェクトのライフサイクル {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

作成した時点から、 `PTMediaPlayer` インスタンスを終了（再利用または削除）した瞬間に、このインスタンスは、あるステータスから別のステータスへの一連の遷移を完了します。

一部の操作は、プレーヤーが特定の状態にある場合にのみ許可されます。 例： `play` in `PTMediaPlayerStatusCreated` は許可されていません。 このステータスは、プレーヤーが `PTMediaPlayerStatusReady` ステータス。

ステータスを処理するには：

* MediaPlayer オブジェクトの現在のステータスは、 `PTMediaPlayer.status`.
* ステータスのリストは、 `PTMediaPlayerStatus`.

MediaPlayer インスタンスのライフサイクルの状態遷移図です。
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

その他の詳細を次の表に示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>PTMediaPlayerStatus</b></th> 
   <th colname="col2" class="entry"><b>発生するタイミング</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが <span class="codeph"> playerWithMediaPlayerItem</span>. 新しく作成されたプレーヤーは、メディアプレーヤーアイテムの指定を待っています。 これは、メディアプレーヤーの初期ステータスです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションの呼び出し <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>、メディアプレーヤーが読み込まれている状態。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDK は、メディアプレーヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入された、または広告手順が失敗した。 バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがを呼び出しました <span class="codeph"> play</span>そのため、 TVSDK はビデオを再生しようとしています。 ビデオが実際に再生される前にバッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレーヤーはこの状態と <span class="codeph"> PTMediaPlayerStatusPlaying</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>プレーヤーがストリームの終わりに到達し、再生が停止した。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStopped</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレーヤーをリリースし、関連するリソースもリリースしました。 このインスタンスは使用できなくなりました </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える場合があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに関するフィードバックを提供したり（例えば、次のステータスの変更を待つ間は、スピナーを表示）、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアを再生する際に次の手順を実行できます。
