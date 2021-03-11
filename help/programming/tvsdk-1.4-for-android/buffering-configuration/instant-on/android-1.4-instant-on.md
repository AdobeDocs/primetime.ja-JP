---
description: 即時オンという用語は、1つ以上のチャネルをプリロードすることを指し、チャネルを選択したり、チャネルを切り替えたりした場合に、コンテンツがすぐに再生されるのを目的とします。 バッファリングは、ユーザー開始が視聴している時間までに既に行われています。
title: 即時オン
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# {#instant-on}の瞬間

即時オンという用語は、1つ以上のチャネルをプリロードすることを指し、チャネルを選択したり、チャネルを切り替えたりした場合に、コンテンツがすぐに再生されるのを目的とします。 バッファリングは、ユーザー開始が視聴している時間までに既に行われています。

すぐにオンにならない場合、TVSDKは再生するメディアを初期化しますが、開始が`play`を呼び出すまで、ストリームをバッファリングしません。 バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 即時オンにすると、複数のメディアプレイヤー（またはメディアプレイヤーアイテムローダー）インスタンスを起動でき、TVSDK開始はストリームを直ちにバッファリングできます。

ユーザーがチャネルを変更し、ストリームが正しくバッファリングされた場合、新しいチャネル開始ーで即座に`play`を呼び出します。

TVSDKが実行できる`MediaPlayer`インスタンスの数に制限はありませんが、実行するインスタンス数が増えると、より多くのリソースを消費します。 アプリケーションのパフォーマンスは、実行中のインスタンス数の影響を受ける場合があります。 これらのインスタンスについて詳しくは、[MediaPlayerItemLoaderを使用したメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md)を参照してください。

## 即時オン再生用のバッファリングの設定{#configure-buffering-for-instant-on-playback}

即時にオンにすると、チャネルと再生開始を待ち時間なく、即座に切り替えることができます。 即時オンを有効にすると、TVSDKは、再生が開始する前に1つ以上のチャネルをバッファリングします。

1. 状態がPREPAREDであることを確認し、リソースが読み込まれ、再生の準備ができていることを確認します。
1. `play`を呼び出す前に、各`MediaPlayer`インスタンスに対して`prepareBuffer`を呼び出します。

   これにより、即時オンが有効になります。つまり、TVSDK開始は、メディアリソースを実際に再生することなくバッファリングを行います。 TVSDKは、バッファーがいっぱいになると`BUFFERING_COMPLETED`イベントをディスパッチします。

   >[!NOTE]
   >
   >デフォルトでは、`prepareBuffer`と`prepareToPlay`は、最初から再生する開始へのメディアストリームを設定します。 別の位置で開始するには、位置（ミリ秒）を`prepareToPlay`に渡します。

   ```java
   @Override 
   public void onStateChanged(MediaPlayer.PlayerState state,  
                              MediaPlayerNotification notification) { 
       switch (state) { 
           case INITIALIZED: 
               // By default, prepareToPlay and prepareBuffer buffer and start playing 
               // from the beginning of the stream. To start at another position, 
               // pass it into prepareToPlay. This example starts 5 seconds into the stream. 
               _mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               _mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. `BUFFERING_COMPLETE`イベントを受け取ると、開始がアイテムを再生したり、コンテンツが完全にバッファーされたことを示す視覚的なフィードバックを表示したりします。

   `play`を呼び出すと、再生はすぐに開始されます。

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
