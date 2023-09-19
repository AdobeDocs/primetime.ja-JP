---
description: 即時オンを有効にすると、1 つ以上のチャネルがプリロードされます。 ユーザーがチャネルを選択したり、チャネルを切り替えたりすると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが視聴を開始するまでに完了します。
title: 即時オン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# 即時オン {#instant-on}

即時オンを有効にすると、1 つ以上のチャネルがプリロードされます。 ユーザーがチャネルを選択したり、チャネルを切り替えたりすると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが視聴を開始するまでに完了します。

Instant On を指定しないと、 TVSDK は再生するメディアを初期化しますが、アプリケーションがを呼び出すまで、ストリームのバッファリングは開始しません `play`. バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 即時オンにすると、複数のメディアプレーヤー（またはメディアプレーヤーアイテムローダー）インスタンスを起動でき、 TVSDK はストリームのバッファリングを直ちに開始します。 ユーザーがチャネルを変更し、ストリームが正しくバッファーされた場合、 `play` 新しいチャネルでは、再生が直ちに開始されます。

ただし、 `MediaPlayer` および `MediaPlayerItemLoader` TVSDK が実行できるインスタンスの数が増えると、実行するインスタンスの数が増え、多くのリソースが消費されます。 実行中のインスタンスの数によって、アプリケーションのパフォーマンスが影響を受ける場合があります。 詳しくは、 `MediaPlayerItemLoader`を参照してください。 [メディアプレーヤーへのメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md).

>[!IMPORTANT]
>
>TVSDK は、単一の `QoSProvider` 両者を相手に働く `itemLoader` および `MediaPlayer`. お客様がインスタントオンを使用する場合、アプリケーションは 2 つの QoS インスタンスを維持し、情報の両方のインスタンスを管理する必要があります。

詳しくは、 `MediaPlayerItemLoader`を参照してください。 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## QoS Provider インスタンスを mediaPlayerItemLoader に追加する {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* QoS プロバイダーの作成とへの接続 `mediaPlayerItemLoader` インスタンス

  ```
  // Create an instance of QoSProvider  
  private QOSProvider _qosProvider = new QOSProvider(this._context);  
  
  // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
  // (before calling load API on mediaPlayerItemLoader instance)  
  _qosProvider.attachMediaPlayerItemLoader(this._loader); 
  ```

  再生が開始したら、 `_qosProvider` 手に入れる `timeToLoad` および `timeToPrepare` QoSdata。 残りの QoS 指標は、 `QoSProvider` ～に付随する `mediaPlayer`.

  詳しくは、 `MediaPlayerItemLoader`を参照してください。 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

## 即時オンでのバッファリングの設定 {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDK は、メディアリソースでインスタントオンを使用できるメソッドとステータスを提供します。

>[!NOTE]
>
>Adobeは、 `MediaPlayerItemLoader` InstantOn の場合 次を使用するには： `MediaPlayerItemLoader`ではなく `MediaPlayer`を参照してください。 [MediaPlayerItemLoader を使用したメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md).

1. リソースが読み込まれ、プレーヤーがリソースを再生する準備が整っていることを確認します。
1. 呼び出し前 `play`，呼び出し `prepareBuffer` 次の期間 `MediaPlayer` インスタンス。

   `prepareBuffer` 即時オンを有効にすると、 TVSDK は即座にバッファリングを開始し、 `BUFFERING_COMPLETED` イベントを返します。

   >[!TIP]
   >
   >デフォルトでは、 `prepareBuffer` および `prepareToPlay` メディアストリームを設定して、最初から再生を開始します。 別の位置から開始するには、位置（ミリ秒）をに渡します。 `prepareToPlay`.

   ```
   @Override 
   public void onStatusChanged(MediaPlayerStatus status) { 
       switch (status) { 
           case INITIALIZED: 
               // This example starts 5 seconds into the stream. 
               mediaPlayer.prepareToPlay(5000); 
               break; 
           case PREPARING: 
               break; 
           case PREPARED: 
               mediaPlayer.prepareBuffer(); 
               break; 
           ... 
       } 
   }
   ```

1. 次を受け取ったとき： `BUFFERING_COMPLETE` イベントを呼び出し、コンテンツが完全にバッファーされたことを示す視覚的なフィードバックを表示します。

   >[!NOTE]
   >
   >を呼び出す場合 `play`、再生は直ちに開始されます。
