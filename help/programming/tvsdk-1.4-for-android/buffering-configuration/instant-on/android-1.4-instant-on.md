---
description: 「即時オン」という用語は、チャネルを選択するユーザーがコンテンツをすぐに再生できるように、1 つ以上のチャネルをプリロードすることを指します。 バッファリングは、ユーザーが視聴を開始するまでに既におこなわれています。
title: 即時オン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# 即時オン {#instant-on}

「即時オン」という用語は、チャネルを選択するユーザーがコンテンツをすぐに再生できるように、1 つ以上のチャネルをプリロードすることを指します。 バッファリングは、ユーザーが視聴を開始するまでに既におこなわれています。

すぐにオンにならない場合、 TVSDK は、再生するメディアを初期化しますが、アプリケーションがを呼び出すまで、ストリームのバッファリングは開始しません `play`. バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 すぐにオンにすると、複数のメディアプレーヤー（またはメディアプレーヤーアイテムローダー）インスタンスを起動でき、 TVSDK はストリームのバッファリングを直ちに開始します。

ユーザーがチャネルを変更し、ストリームが正しくバッファーされた場合、 `play` 新しいチャネルでは、再生が直ちに開始されます。

ただし、 `MediaPlayer` TVSDK が実行できるインスタンスの数が増えると、実行するインスタンスの数が増え、多くのリソースが消費されます。 アプリケーションのパフォーマンスは、実行中のインスタンスの数の影響を受ける場合があります。 これらのインスタンスについて詳しくは、 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-1.4-for-android/ui-configure/mediaplayer-initialize-for-video/android-1.4-media-mediaplayeritemloader.md).

## 即時オン再生用のバッファリングの設定 {#configure-buffering-for-instant-on-playback}

すぐにオンにすると、ユーザーはチャネルを切り替え、待ち時間をかけずにすぐに再生を開始できます。 即時オンを有効にすると、 TVSDK は、再生が開始される前に 1 つ以上のチャネルをバッファリングします。

1. リソースが読み込まれ、状態が PREPARED であることを確認し、再生の準備ができていることを確認します。
1. 呼び出し前 `play`，呼び出し `prepareBuffer` 次の期間 `MediaPlayer` インスタンス。

   これにより、即時オンが有効になります。つまり、 TVSDK は、実際にメディアリソースを再生せずにバッファリングを開始します。 TVSDK が `BUFFERING_COMPLETED` イベントを返します。

   >[!NOTE]
   >
   >デフォルトでは、 `prepareBuffer` および `prepareToPlay` メディアストリームを設定して、最初から再生を開始します。 別の位置から開始するには、次の場所（ミリ秒）を `prepareToPlay`.

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

1. 次を受け取ったとき： `BUFFERING_COMPLETE` イベントを呼び出し、コンテンツが完全にバッファーされたことを示す視覚的なフィードバックを表示します。

   を呼び出す場合 `play`、再生は直ちに開始されます。

   ```java
   void onBufferPrepared(const psdk::PSDKEvent *ev) { 
       mediaPlayer->play(); 
   }
   ```
