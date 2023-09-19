---
description: メディアプレーヤーのステータスによって、どのアクションが有効かが決まります。
title: MediaPlayer オブジェクトのライフサイクルとステータス
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MediaPlayer オブジェクトのライフサイクルとステータス{#lifecycle-and-statuses-of-the-mediaplayer-object}

メディアプレーヤーのステータスによって、どのアクションが有効かが決まります。

メディアプレーヤーのステータスを操作する場合：

* 現在のステータスを取得するには、 `MediaPlayer` ～に対して `MediaPlayer.getStatus()`.

* ステータスのリストは、 [MediaPlayerStatus](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.5/com/adobe/mediacore/MediaPlayerStatus.html) enum.

のライフサイクルのステータス遷移図 `MediaPlayer` インスタンス：

<!--<a id="fig_A6425F24C7734DC681D992859D2A6743"></a>-->

![](assets/media_player_statuses.png)

次の表に、メディアプレーヤーのライフサイクルとステータスの詳細を示します。

<table id="table_82757A0043EB4AACA474E6B30326A6B7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> ステータス </th> 
   <th colname="col2" class="entry"> 発生するタイミング </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> アイドル </td> 
   <td colname="col2"> <p>メディアプレーヤーの初期ステータス。 プレーヤーが作成され、メディアプレーヤーアイテムの指定を待機しています。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 初期化中 </td> 
   <td colname="col2"> <p>アプリケーションの呼び出し <span class="codeph"> MediaPlayer.replaceCurrentItem() </span>. </p> <p>メディアプレーヤーアイテムを読み込んでいます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 初期化済み </td> 
   <td colname="col2"> <p>TVSDK は media-player 項目を正常に設定しました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 準備中 </td> 
   <td colname="col2"> <p>アプリケーションの呼び出し <span class="codeph"> MediaPlayer.prepareToPlay() </span>. メディアプレーヤーは、メディアプレーヤーアイテムと関連するリソースを読み込みます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 準備済み </td> 
   <td colname="col2"> <p>TVSDK は、メディアストリームを準備し、広告解決と広告挿入（有効な場合）を実行しようとしました。 コンテンツが準備され、広告がタイムラインに挿入された、または広告手順が失敗した。 </p> <p>バッファリングまたは再生を開始できます。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 再生中/一時停止中 </td> 
   <td colname="col2"> <p>アプリケーションがメディアを再生および一時停止すると、メディアプレーヤーはこれらのステータス間を移動します。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 中断 </td> 
   <td colname="col2"> <p>プレーヤーの再生中または一時停止中にアプリケーションが再生から離脱したり、デバイスをシャットダウンしたり、アプリケーションを切り替えたりすると、メディアプレーヤーは停止され、リソースが解放されます。 </p> <p>呼び出し <span class="codeph"> MediaPlayer.restore() </span> は、プレーヤーが SUSPENDED になる前の状態にプレーヤーを返します。 例外は、休止状態が呼び出されたときにプレーヤーが SEEK 状態の場合、プレーヤーは PAUSED になり、その後 SUSPENDED になります。 </p> <p>重要：  <p>次の情報に留意してください。 
      <ul id="ul_1B21668994D1474AAA0BE839E0D69B00"> 
       <li id="li_08459A3AB03C45588D73FA162C27A56C">The <span class="codeph"> MediaPlayer </span> 自動呼び出し <span class="codeph"> 休止 </span> は、 <span class="codeph"> MediaPlayerView </span> が破壊されました。 </li> 
       <li id="li_B9926AA2E7B9441490F37D24AE2678A1">The <span class="codeph"> MediaPlayer </span> 自動呼び出し <span class="codeph"> restore() </span> 新しいサーフェスオブジェクトが <span class="codeph"> MediaPlayerView </span> が作成されました。 </li> 
      </ul> </p> </p> <p>MediaPlayer が復元されたときに再生を常に一時停止する場合は、アプリケーションでを呼び出してください <span class="codeph"> MediaPlayer.pause() </span> Android アクティビティの <span class="codeph"> onPause() </span> メソッド。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 完了 </td> 
   <td colname="col2"> <p>プレーヤーがストリームの終わりに到達し、再生が停止した。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> リリース済み </td> 
   <td colname="col2"> <p>アプリケーションがメディアプレーヤーをリリースし、関連するリソースもリリースします。 このインスタンスは使用できなくなりました。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> エラー </td> 
   <td colname="col2"> <p>プロセス中にエラーが発生しました。 また、エラーは、アプリケーションが次に実行できる操作に影響を与える可能性があります。 詳しくは、 <a href="../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/android-3x-error-handling-set-up.md" format="dita" scope="local"> エラー処理の設定 </a>. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!TIP]
>
>ステータスを使用して、プロセスに関するフィードバックを提供したり、次のステータスの変更を待つ間にスピナーを表示したり、次のメソッドを呼び出す前に適切なステータスを待つなど、メディアを再生する際に次の手順を実行したりできます。

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
