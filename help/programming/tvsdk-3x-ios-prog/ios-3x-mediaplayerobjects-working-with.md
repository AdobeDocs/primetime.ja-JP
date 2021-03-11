---
description: PTMediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 PTMediaPlayerItemは、プレイヤー上のオーディオまたはビデオを表します。
title: MediaPlayerオブジェクトの操作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# MediaPlayerオブジェクトの操作{#work-with-mediaplayer-objects}

PTMediaPlayerオブジェクトは、使用するメディアプレイヤーを表します。 PTMediaPlayerItemは、プレイヤー上のオーディオまたはビデオを表します。

## MediaPlayerItemクラス{#section_B6F36C0462644F5C932C8AA2F6827071}について

メディアリソースが正常に読み込まれた後、TVSDKは`PTMediaPlayerItem`クラスのインスタンスを作成して、そのリソースへのアクセスを提供します。

`PTMediaPlayer`は、メディアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 `PTMediaPlayerItem`インスタンスは、リソースが解決された後に生成され、このインスタンスはメディアリソースの解決されたバージョンです。 TVSDKは、新しく作成された`PTMediaPlayerItem`インスタンスに対して、`PTMediaPlayer.currentItem`を介してアクセスを提供します。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤーアイテムにアクセスする必要があります。

## MediaPlayerオブジェクトのライフサイクル{#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

`PTMediaPlayer`インスタンスを作成した瞬間から終了（再利用または削除）した瞬間まで、このインスタンスはあるステータスから別のステータスへの一連のトランジションを完了します。

一部の操作は、プレイヤーが特定の状態にある場合にのみ許可されます。 例えば、`PTMediaPlayerStatusCreated`で`play`を呼び出すことはできません。 このステータスは、プレイヤーが`PTMediaPlayerStatusReady`ステータスに達した後にのみ呼び出すことができます。

ステータスを使用するには：

* `PTMediaPlayer.status`を使用して、MediaPlayerオブジェクトの現在のステータスを取得できます。
* ステータスのリストは`PTMediaPlayerStatus`に定義されています。

MediaPlayerインスタンスのライフサイクルの状態トランジション図：
<!--<a id="fig_1C55DE3F186F4B36AFFDCDE90379534C"></a>-->

![](assets/player-state-transitions-diagram-ios2_web.png)

次の表に、その他の詳細を示します。

<table id="table_426F0093E4214EA88CD72A7796B58DFD"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>PTMediaPlayerStatus</b></th> 
   <th colname="col2" class="entry"><b>発生するのは</b> </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCreated</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが、<span class="codeph"> playerWithMediaPlayerItem</span>を呼び出して新しいメディアプレイヤーを要求しました。 新しく作成されたプレイヤーは、ユーザーがメディアプレイヤーアイテムを指定するのを待っています。 これは、メディアプレイヤーの初期ステータスです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが<span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>を呼び出し、メディアプレイヤーが読み込まれます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入されているか、広告手順が失敗しています。 バッファリングまたは再生が開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが<span class="codeph"> play</span>を呼び出したので、TVSDKはビデオを再生しようとしています。 ビデオが実際に再生される前に、バッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこの状態と<span class="codeph"> PTMediaPlayerStatusPlaying</span>の間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>プレイヤーがストリームの終わりに到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStopped</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連付けられているリソースもすべて解放します。 このインスタンスは使用できなくなります </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響する可能性があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに対するフィードバック（例えば、次のステータス変更を待つ間のスピナー）を提供したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアの再生時に次の手順を実行したりできます。