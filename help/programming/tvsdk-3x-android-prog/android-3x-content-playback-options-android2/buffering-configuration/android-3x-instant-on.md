---
description: 即時オンを有効にすると、1つ以上のチャネルがプリロードされます。 ユーザーがチャネルまたはチャネルを切り替えると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが視聴を開始するまでに完了します。
seo-description: 即時オンを有効にすると、1つ以上のチャネルがプリロードされます。 ユーザーがチャネルまたはチャネルを切り替えると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが視聴を開始するまでに完了します。
seo-title: 即時オン
title: 即時オン
uuid: 5b1ceace-cae7-44c7-b4b9-d45078d58cc3
translation-type: tm+mt
source-git-commit: ed910a60440ae7c0d19d9be56c80c8bdbc62bcf1

---


# 即時オン {#instant-on}

即時オンを有効にすると、1つ以上のチャネルがプリロードされます。 ユーザーがチャネルまたはチャネルを切り替えると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが視聴を開始するまでに完了します。

即時オンを指定しない場合、TVSDKは再生するメディアを初期化しますが、アプリケーションが呼び出すまでストリームのバッファリングを開始しませ `play`ん。 バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 即時オンを使用すると、複数のメディアプレイヤー（またはメディアプレイヤーアイテムローダー）インスタンスを起動でき、TVSDKはストリームのバッファリングを即座に開始します。 ユーザーがチャネルを変更し、ストリームが正しくバッファーされた場合、新しいチャネルを呼び出す `play` と、即座に再生が開始されます。

TVSDKが実行できるインスタンスの数と数に制限はあり `MediaPlayer` ませんが、 `MediaPlayerItemLoader` 実行するインスタンスの数が多いと、より多くのリソースが消費されます。 アプリケーションのパフォーマンスは、実行中のインスタンスの数に影響を受ける可能性があります。 詳しくは、メディアプレ `MediaPlayerItemLoader`イヤーへ [のメディアリソースの読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md)。

>[!IMPORTANT]
>
>TVSDKは、との両方で機能する単一 `QoSProvider` のTVSDKをサポートして `itemLoader` いませ `MediaPlayer`ん。 顧客が即時オンを使用する場合、アプリケーションは2つのQoSインスタンスを維持し、情報の両方のインスタンスを管理する必要があります。

詳しくは、MediaPlayerItemLoaderを使用したメ `MediaPlayerItemLoader`ディアリ [ソースの読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)。

## QoSプロバイダーインスタンスをmediaPlayerItemLoaderに追加します {#section_2F9F24C7BFAD49599D043D64F767F9A0}

* QoSプロバイダーの作成とインスタンスへのアタ `mediaPlayerItemLoader` ッチ

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   再生が開始したら、を使用して `_qosProvider` QoSdataを取 `timeToLoad` 得し `timeToPrepare` ます。 残りのQoS指標は、に添付されたを使用して `QoSProvider` 取得できます `mediaPlayer`。

   詳しくは、MediaPlayerItemLoaderを使用したメ `MediaPlayerItemLoader`ディアリ [ソースの読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)。

## 即時オンのバッファリングの設定 {#section_4FE346B7BE434BA8A2203896D6E52146}

TVSDKは、メディアリソースでインスタントオンを使用できるメソッドとステータスを提供します。

>[!NOTE]
>
>アドビでは、InstantOn用の使用をお `MediaPlayerItemLoader` 勧めしています。 使用する方法につ `MediaPlayerItemLoader`いては、MediaPlayerItemLoaderを使用 `MediaPlayer`したメディアリ [ソースの読み込みを参照してください](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)。

1. リソースが読み込まれ、プレイヤーがリソースを再生する準備ができていることを確認します。
1. 呼び出す前に、 `play`各インスタ `prepareBuffer` ンスに対してを呼び出 `MediaPlayer` します。

   `prepareBuffer` 即時オンを有効にし、TVSDKはバッファリングを直ちに開始し、バッファーがいっぱいにな `BUFFERING_COMPLETED` ったらイベントをディスパッチします。

   >[!TIP]
   >
   >デフォルトでは、 `prepareBuffer` 最初か `prepareToPlay` ら再生を開始するようにメディアストリームを設定します。 別の位置から開始するには、位置（ミリ秒）をに渡します `prepareToPlay`。

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

1. イベントを受け取ったら、 `BUFFERING_COMPLETE` アイテムの再生を開始するか、コンテンツが完全にバッファされたことを示す視覚的なフィードバックを表示します。

   >[!NOTE]
   >
   >を呼び出すと、再 `play`生はすぐに開始されます。