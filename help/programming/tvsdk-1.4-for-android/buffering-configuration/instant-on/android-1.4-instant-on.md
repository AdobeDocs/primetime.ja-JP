---
description: 「即時オン」とは、1つ以上のチャネルをプリロードすることで、チャネルを選択したユーザやチャネルを切り替えたユーザが直ちに再生中のコンテンツを見ることを意味します。 バッファリングは、ユーザーが視聴を開始するまでに既に行われています。
seo-description: 「即時オン」とは、1つ以上のチャネルをプリロードすることで、チャネルを選択したユーザやチャネルを切り替えたユーザが直ちに再生中のコンテンツを見ることを意味します。 バッファリングは、ユーザーが視聴を開始するまでに既に行われています。
seo-title: 即時オン
title: 即時オン
uuid: 4cb4d221-170f-46e8-af26-32f259377617
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 即時オン {#instant-on}

「即時オン」とは、1つ以上のチャネルをプリロードすることで、チャネルを選択したユーザやチャネルを切り替えたユーザが直ちに再生中のコンテンツを見ることを意味します。 バッファリングは、ユーザーが視聴を開始するまでに既に行われています。

即時にオンにすると、TVSDKは再生するメディアを初期化しますが、アプリケーションが呼び出されるまでストリームのバッファリングを開始しませ `play`ん。 バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 即時オンにすると、複数のメディアプレイヤー（またはメディアプレイヤーアイテムローダー）インスタンスを起動でき、TVSDKはストリームのバッファリングを直ちに開始します。

ユーザーがチャネルを変更し、ストリームが正しくバッファーされた場合、新しいチャネルを呼び出す `play` と、即座に再生が開始されます。

TVSDKが実行できるインスタンスの数に制限はありませ `MediaPlayer` んが、実行するインスタンスの数が増えると、より多くのリソースが消費されます。 アプリケーションのパフォーマンスは、実行中のインスタンスの数に影響を受ける可能性があります。 これらのインスタンスについて詳しくは、MediaPlayerItemLoaderを使用したメ [ディアリソースの読み込みを参照してください](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md)。

## 即時オン再生のバッファリングの設定 {#configure-buffering-for-instant-on-playback}

即時オンにすると、ユーザーはチャネルを切り替え、待ち時間なしで再生をすぐに開始できます。 即時オンを有効にすると、TVSDKは再生が開始される前に1つ以上のチャネルをバッファリングします。

1. リソースが読み込まれ、再生の準備ができていることを確認します。状態がPREPAREDであることを確認します。
1. 呼び出す前に、 `play`各インスタ `prepareBuffer` ンスに対してを呼び出 `MediaPlayer` します。

   これにより、即時オンが有効になります。つまり、TVSDKは、実際にメディアリソースを再生せずにバッファリングを開始します。 TVSDKは、バッファーがいっぱ `BUFFERING_COMPLETED` いになると、イベントをディスパッチします。

   >[!NOTE]
   >
   >デフォルトでは、 `prepareBuffer` 最初か `prepareToPlay` ら再生を開始するようにメディアストリームを設定します。 別の位置から開始するには、位置（ミリ秒）をに渡します `prepareToPlay`。

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

1. イベントを受け取ったら、 `BUFFERING_COMPLETE` アイテムの再生を開始するか、コンテンツが完全にバッファされたことを示す視覚的なフィードバックを表示します。

   を呼び出すと、再 `play`生はすぐに開始されます。

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
