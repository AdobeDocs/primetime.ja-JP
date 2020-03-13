---
description: メディアプレイヤーのステータスによって、どのアクションが有効かが決まります。
seo-description: メディアプレイヤーのステータスによって、どのアクションが有効かが決まります。
seo-title: MediaPlayerオブジェクトのライフサイクルとステータス
title: MediaPlayerオブジェクトのライフサイクルとステータス
uuid: a2866f84-a722-46ed-b4cb-36664db5be82
translation-type: tm+mt
source-git-commit: 56dc79e5b4df11ff730d7d8f23dea8d0f4712077

---


# MediaPlayerオブジェクトのライフサイクルとステータス{#lifecycle-and-statuses-of-the-mediaplayer-object}

メディアプレイヤーのステータスによって、どのアクションが有効かが決まります。

メディアプレイヤーのステータスを操作する場合：

* でオブジェクトの現在のステータスを取得 `MediaPlayer` できま `MediaPlayer.getStatus()`す。

* ステータスのリストは、MediaPlayerStatus列挙で定義さ [れます](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html) 。

インスタンスのライフサイクルのステータス遷移図 `MediaPlayer` :

<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

次の表に、メディアプレイヤーのライフサイクルとステータスの詳細を示します。

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ステータス </th> 
   <th colname="col2" class="entry"> 発生するのは </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> IDLE </td> 
   <td colname="col2"> <p>メディアプレイヤーの初期ステータス。 プレイヤーが作成され、メディアプレイヤー項目の指定を待機しています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 初期化中 </td> 
   <td colname="col2"> <p>アプリケーション <span class="codeph"> がMediaPlayer.replaceCurrentItem()を呼び出しま </span>す。 </p> <p>メディアプレイヤー項目を読み込んでいます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALIZED </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤー項目を正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 準備中 </td> 
   <td colname="col2"> <p>アプリケーション <span class="codeph"> がMediaPlayer.prepareToPlay()を呼び出しま </span>す。 メディアプレイヤーは、メディアプレイヤー項目と関連するリソースを読み込んでいます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PREPARED </td> 
   <td colname="col2"> <p>TVSDKは、メディアストリームを準備し、広告解決と広告挿入を実行しようとしました（有効な場合）。 コンテンツが準備され、広告がタイムラインに挿入されているか、広告の手順が失敗した。 </p> <p>バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 再生/一時停止 </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこれらのステータス間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 休止 </td> 
   <td colname="col2"> <p>再生から離れたり、デバイスをシャットダウンしたり、プレーヤーの再生中または一時停止中にアプリケーションを切り替えたりすると、メディアプレイヤーは停止され、リソースが解放されます。 </p> <p>MediaPlayer.restore() <span class="codeph"> を呼び出すと、プ </span> レイヤーはSUSPENDEDの前の状態に戻ります。 例外は、休止中のプレイヤーが呼び出されたときにシーク中の場合、そのプレイヤーは一時停止され、次に休止中です。 </p> <p>重要：  <p>次の情報を記憶しておきます。 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">MediaPlayerViewで使用され <span class="codeph"> ている表面オ </span> ブジェクトが破棄された場合にのみ、MediaPlayerが <span class="codeph"> 自動的に中断 </span><span class="codeph"></span> を呼び出します。 </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">MediaPlayerViewで使用さ <span class="codeph"> れる新し </span> いサーフェスオ <span class="codeph"> ブジェクトが作成された場合にのみ、 </span> MediaPlayerは自動的にrestore()を呼び出 <span class="codeph"></span> します。 </li> 
      </ul> </p> </p> <p>MediaPlayerの復元時に再生を常に一時停止する場合は、Android Activityの <span class="codeph"> onPause()メソッドで、アプリケーシ </span> ョンからMediaPlayer.pause()を呼び出す <span class="codeph"> ようにし </span> ます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 完了 </td> 
   <td colname="col2"> <p>プレイヤーがストリームの終わりに到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> RELEASED </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連するリソースもすべて解放しました。 このインスタンスは使用できなくなりました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> エラー </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える可能性があります。 詳しくは、エラー処理の設 <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> 定を参照してくださ </a>い。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに関するフィードバック、例えば、次のステータス変更を待つ間のスピナーを表示したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアの再生時に次の手順を実行したりできます。

例：

```java
mediaPlayer.addEventListener(MediaPlayerEvent STATUS_CHANGED, new StatusChangeEventListener() { 
    @Override  
    public void onStatusChanged(MediaPlayerStatusChangeEvent event) { 
        switch(event.getStatus()) { 
            case INITIALIZED: 
                mediaPlayer.prepareToPlay(); 
                break; 
            case PREPARING: 
                showBufferingSpinner(); 
                break; 
            case PREPARED: 
                hideBufferingSpinner(); 
                mediaPlayer.play(); 
                break; 
            ...                
        } 
        ... 
    } 
}); 
```
