---
description: メディアプレイヤーのステータスによって、どのアクションが有効かが決まります。
title: MediaPlayerオブジェクトのライフサイクルとステータス
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---


# MediaPlayerオブジェクトのライフサイクルとステータス{#lifecycle-and-statuses-of-the-mediaplayer-object}

メディアプレイヤーのステータスによって、どのアクションが有効かが決まります。

メディアプレイヤーのステータスを操作する場合：

* `MediaPlayer.getStatus()`を使用して、`MediaPlayer`オブジェクトの現在のステータスを取得できます。

* ステータスのリストは、[MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html)列挙で定義されています。

`MediaPlayer`インスタンスのライフサイクルのステータストランジション図：

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
   <td colname="col2"> <p>メディアプレイヤーの初期ステータス。 プレイヤーが作成され、メディアプレイヤーアイテムの指定を待っています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 初期化中 </td> 
   <td colname="col2"> <p>アプリケーションが<span class="codeph"> MediaPlayer.replaceCurrentItem() </span>を呼び出します。 </p> <p>メディアプレイヤーアイテムを読み込んでいます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> INITIALIZED </td> 
   <td colname="col2"> <p>TVSDKは、メディアプレイヤーアイテムを正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 準備中 </td> 
   <td colname="col2"> <p>アプリケーションが<span class="codeph"> MediaPlayer.prepareToPlay() </span>を呼び出します。 メディアプレイヤーは、メディアプレイヤーアイテムおよび関連するリソースを読み込んでいます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> PREPARED </td> 
   <td colname="col2"> <p>TVSDKは、メディアストリームを準備し、広告解決と広告挿入を実行しようとしました（有効な場合）。 コンテンツが準備され、広告がタイムラインに挿入されているか、広告手順が失敗しています。 </p> <p>バッファリングまたは再生が開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 再生/一時停止中 </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレイヤーはこれらのステータス間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 休止 </td> 
   <td colname="col2"> <p>再生中または一時停止中に、アプリケーションが再生から離れたり、デバイスをシャットダウンしたり、アプリケーションを切り替えたりした場合、メディアプレイヤーは中断され、リソースは解放されます。 </p> <p><span class="codeph"> MediaPlayer.restore() </span>を呼び出すと、プレイヤーがSUSPENDEDの前の状態に戻ります。 例外は、休止状態が呼び出されたときにプレイヤーがSEEKINGを行っている場合、プレイヤーはPAUSEDの後、SUSPENDEDになります。 </p> <p>重要：  <p>次の情報を覚えておいてください。 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C"><span class="codeph"> MediaPlayer </span>は、<span class="codeph"> MediaPlayerView </span>で使用されるサーフェスオブジェクトが破棄された場合にのみ、<span class="codeph"> suspend </span>を自動的に呼び出します。 </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1"><span class="codeph"> MediaPlayer </span>は、<span class="codeph"> MediaPlayerView </span>で使用される新しいサーフェスオブジェクトが作成された場合にのみ、<span class="codeph"> restore() </span>を自動的に呼び出します。 </li> 
      </ul> </p> </p> <p>MediaPlayerの復元時に再生を常に一時停止する場合は、Androidアクティビティの<span class="codeph"> onPause() </span>メソッドで、アプリケーションの呼び出し<span class="codeph"> MediaPlayer.pause() </span>を使用してください。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 完了 </td> 
   <td colname="col2"> <p>プレイヤーがストリームの終わりに到達し、再生が停止しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> RELEASED </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレイヤーをリリースし、関連付けられているリソースも解放します。 このインスタンスは使用できなくなります。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> ERROR </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 エラーは、アプリケーションが次に実行できる操作に影響する場合もあります。 詳しくは、<a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local">エラー処理の設定</a>を参照してください。 </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに対するフィードバックを提供したり、次のステータス変更を待つ間にスピナーを表示したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアの再生時に次の手順を実行したりできます。

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
