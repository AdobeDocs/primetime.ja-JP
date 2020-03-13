---
description: PTMediaPlayerオブジェクトは、メディアプレイヤーを表します。 PTMediaPlayerItemは、プレイヤー上のオーディオまたはビデオを表します。
seo-description: PTMediaPlayerオブジェクトは、メディアプレイヤーを表します。 PTMediaPlayerItemは、プレイヤー上のオーディオまたはビデオを表します。
seo-title: MediaPlayerオブジェクトの操作
title: MediaPlayerオブジェクトの操作
uuid: 0c33ebd6-b11a-4e62-8c1c-880cfceff474
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# MediaPlayerオブジェクトの操作 {#work-with-mediaplayer-objects}

PTMediaPlayerオブジェクトは、メディアプレイヤーを表します。 PTMediaPlayerItemは、プレイヤー上のオーディオまたはビデオを表します。

## MediaPlayerItemクラスについて {#section_B6F36C0462644F5C932C8AA2F6827071}

メディアリソースが正常に読み込まれた後、TVSDKは、そのリソースへのアクセスを提供 `PTMediaPlayerItem` するクラスのインスタンスを作成します。

は、メデ `PTMediaPlayer` ィアリソースを解決し、関連付けられたマニフェストファイルを読み込み、マニフェストを解析します。 これは、リソース読み込みプロセスの非同期部分です。 このイ `PTMediaPlayerItem` ンスタンスは、リソースが解決された後に生成され、このインスタンスは、メディアリソースの解決されたバージョンです。 TVSDKは、を通じて新しく作成されたインスタンスへのアクセス `PTMediaPlayerItem` を提供しま `PTMediaPlayer.currentItem`す。

>[!TIP]
>
>リソースが正常に読み込まれるのを待ってから、メディアプレイヤー項目にアクセスする必要があります。

## MediaPlayerオブジェクトのライフサイクル {#section_D87EF7FBC7B442BDBE825156DC2C1CCF}

インスタンスを作成した瞬間から終了(再 `PTMediaPlayer` 利用または削除)した瞬間まで、このインスタンスはあるステータスから別のステータスへの一連の遷移を完了します。

一部の操作は、プレイヤーが特定の状態の場合にのみ許可されます。 例えば、での呼び出し `play` は許可 `PTMediaPlayerStatusCreated` されません。 このステータスは、プレイヤーがステータスに達した後でのみ呼び出すことがで `PTMediaPlayerStatusReady` きます。

ステータスを操作するには：

* MediaPlayerオブジェクトの現在のステータスを取得できます `PTMediaPlayer.status`。
* ステータスのリストは、で定義されていま `PTMediaPlayerStatus`す。

MediaPlayerインスタンスのライフサイクルの状態遷移図：
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
   <td colname="col2"> <p>アプリケーションがplayerWithMediaPlayerItemを呼び出して新しいメディアプレイヤーを要 <span class="codeph"> 求しました</span>。 新しく作成されたプレイヤーは、メディアプレイヤー項目の指定を待っています。 これは、メディアプレイヤーの初期ステータスです。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusInitializing</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが <span class="codeph"> PTMediaPlayer.replaceCurrentItemWithPlayerItem</span>を呼び出し、メディアプレイヤーが読み込まれます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusInitialized</span> </p> </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤー項目を正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> PTMediaPlayerStatusReady</span> </p> </td> 
   <td colname="col2"> <p>コンテンツが準備され、広告がタイムラインに挿入されたか、広告手順が失敗した。 バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPlaying</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションが <span class="codeph"> play</span>を呼び出したので、TVSDKはビデオの再生を試みています。 ビデオが実際に再生される前に、バッファリングが発生する場合があります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusPaused</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこの状態とPTMediaPlayerStatusPlayingの間を移 <span class="codeph"> 動します</span>。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusCompleted</span> </p> </td> 
   <td colname="col2"> <p>プレイヤーがストリームの最後に到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusStopped</span> </p> </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連するリソースもすべて解放しました。 このインスタンスは使用できなくなりました </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p><span class="codeph"> PTMediaPlayerStatusError</span> </p> </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える可能性があります。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに対するフィードバック（例えば、次のステータス変更を待つ間のスピナー）を提供したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアの再生時に次の手順を実行したりできます。