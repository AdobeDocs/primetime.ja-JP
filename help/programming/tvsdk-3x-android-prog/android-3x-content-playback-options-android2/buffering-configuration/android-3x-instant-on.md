---
description: 即時オンを有効にすると、1つ以上のチャネルがプリロードされます。 ユーザーがチャネルを選択するかチャネルを切り替えると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが開始を監視するまでに完了します。
title: 即時オン
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# {#instant-on}の瞬間

即時オンを有効にすると、1つ以上のチャネルがプリロードされます。 ユーザーがチャネルを選択するかチャネルを切り替えると、コンテンツは直ちに再生されます。 バッファリングは、ユーザーが開始を監視するまでに完了します。

即時オンを指定しないと、TVSDKは再生するメディアを初期化しますが、開始が`play`を呼び出すまで、ストリームをバッファリングしません。 バッファリングが完了するまで、ユーザーにはコンテンツが表示されません。 即時オンでは、複数のメディアプレイヤー（またはメディアプレイヤーアイテムローダー）インスタンスを起動でき、TVSDK開始はストリームを直ちにバッファリングできます。 ユーザーがチャネルを変更し、ストリームが正しくバッファリングされた場合、新しいチャネル開始ーで即座に`play`を呼び出します。

TVSDKが実行できる`MediaPlayer`および`MediaPlayerItemLoader`のインスタンス数に制限はありませんが、実行するインスタンス数が増えると、より多くのリソースが消費されます。 アプリケーションのパフォーマンスは、実行中のインスタンス数の影響を受ける場合があります。 `MediaPlayerItemLoader`について詳しくは、[メディアプレイヤーへのメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-load.md)を参照してください。

>[!IMPORTANT]
>
>TVSDKは、1つの`QoSProvider`をサポートせず、`itemLoader`と`MediaPlayer`の両方で動作します。 顧客が即時オンを使用する場合、アプリケーションは2つのQoSインスタンスを維持し、情報の両方のインスタンスを管理する必要があります。

`MediaPlayerItemLoader`について詳しくは、[MediaPlayerItemLoaderを使用したメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)を参照してください。

## mediaPlayerItemLoader追加 {#section_2F9F24C7BFAD49599D043D64F767F9A0}に対するQoSプロバイダーインスタンス

* QoSプロバイダーの作成と`mediaPlayerItemLoader`インスタンスへの接続

   ```
   // Create an instance of QoSProvider  
   private QOSProvider _qosProvider = new QOSProvider(this._context);  
   
   // Attach the QoSProvider instance to the mediaPlayerItemLoaderInstance  
   // (before calling load API on mediaPlayerItemLoader instance)  
   _qosProvider.attachMediaPlayerItemLoader(this._loader); 
   ```

   再生開始が終了したら、`_qosProvider`を使用して`timeToLoad`と`timeToPrepare`のQoSdataを取得します。 残りのQoS指標は、`mediaPlayer`に添付された`QoSProvider`を使用して取得できます。

   `MediaPlayerItemLoader`について詳しくは、[MediaPlayerItemLoaderを使用したメディアリソースの読み込み](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)を参照してください。

## {#section_4FE346B7BE434BA8A2203896D6E52146}に即時バッファリングを設定

TVSDKは、メディアリソースでインスタントオンを使用できるメソッドとステータスを提供します。

>[!NOTE]
>
>Adobeでは、InstantOnに`MediaPlayerItemLoader`を使用することを推奨します。 `MediaPlayer`ではなく`MediaPlayerItemLoader`を使用するには、[MediaPlayerItemLoader](../../../tvsdk-3x-android-prog/android-3x-content-playback-options-android2/mediaplayer-initialize-for-video/android-3x-media-resource-mediaplayeritemloader.md)を使用したメディアリソースの読み込みを参照してください。

1. リソースが読み込まれ、プレイヤーがリソースを再生する準備ができていることを確認します。
1. `play`を呼び出す前に、各`MediaPlayer`インスタンスに対して`prepareBuffer`を呼び出します。

   `prepareBuffer` 即時オンを有効にし、TVSDK開始が即座にバッファリングを行い、バッファーがいっぱいになると `BUFFERING_COMPLETED` イベントをディスパッチします。

   >[!TIP]
   >
   >デフォルトでは、`prepareBuffer`と`prepareToPlay`は、最初から再生する開始へのメディアストリームを設定します。 別の位置で開始するには、位置（ミリ秒）を`prepareToPlay`に渡します。

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

1. `BUFFERING_COMPLETE`イベントを受け取ると、開始がアイテムを再生したり、コンテンツが完全にバッファーされたことを示す視覚的なフィードバックを表示したりします。

   >[!NOTE]
   >
   >`play`を呼び出すと、再生はすぐに開始されます。