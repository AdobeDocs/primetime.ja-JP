---
description: TVSDKベースの送信者アプリから任意のストリームをキャストし、そのストリームをブラウザーTVSDKのChromecastで再生できます。
title: Google Castアプリ（ブラウザーTVSDK用）
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Google Cast app for Browser TVSDK{#google-cast-app-for-browser-tvsdk}

TVSDKベースの送信者アプリから任意のストリームをキャストし、そのストリームをブラウザーTVSDKのChromecastで再生できます。

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Cast対応アプリには2つのコンポーネントがあります。

* 送信側アプリケーション。リモートコントロールとして機能します。

   送信者アプリには、スマートフォン、パソコンなどが含まれます。 このアプリは、iOS、Android、Chrome用のネイティブSDKを使用して開発できます。
* 受信者アプリケーション。Chromecastで実行され、コンテンツを再生します。

   >[!IMPORTANT]
   >
   >このアプリは、HTML5アプリにしかできません。

送信者と受信者は、キャストSDKを使用してメッセージを渡すことによって通信します。

## 基本ワークフロー{#section_FAF680FF29DA4D24A50AC0A2B6402B58}

プロセスの概要を次に示します。

1. 送信側のアプリは、受信者のアプリとの接続を確立します。
1. 送信側のアプリは、受信側のアプリにメディアを読み込むためのメッセージを送信します。
1. 受信者アプリは再生を開始します。
1. 送信側のアプリは、再生、一時停止、シーク、早送り、早戻し、巻き戻し、ボリューム変更などの再生制御メッセージを受信側のアプリに送信します。
1. 受信者アプリは、これらのメッセージに反応します。

## メッセージの形式{#section_1624159DD51D4C87B3E5803DEEBCB6B7}

送信者と受信者が理解できるように、メッセージを定義する必要があります。 シークメッセージの例を次に示します。

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

シークメッセージなどのカスタムメッセージをCast SDK経由で送信する場合は、カスタムメッセージ名前空間が必要です。 JavaScriptの例を次に示します。

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## 接続の確立{#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>ブラウザーTVSDK APIは、接続を確立する際には関係しません。

接続を確立するには、送信者と受信者は次のタスクを完了する必要があります。

* 送信者は、[Sender App Development](https://developers.google.com/cast/docs/sender_apps)にあるプラットフォームに関するドキュメントを確認する必要があります。
* 受信者は、Cast受信者APIを使用して、送信者アプリとの接続を確立します。 例：

   ```js
   window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
   
   window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
   
   var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
   customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
   
   window.castReceiverManager.start(); 
   ```

## メッセージ処理{#section_3E4814546F5946C9B3E7A1AE384B4FF8}

受信者にメッセージを送信するには、送信者のプラットフォームに関するドキュメントを参照してください。

>[!IMPORTANT]
>
>すべてのメッセージにカスタムメッセージ名前空間`MSG_NAMESPACE`を含める必要があります。

レシーバーアプリケーションの場合は、キャストレシーバーAPIのドキュメントに従います。

**Chromeベースの送信者メッセージの例**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Chromeベースの送信者イベント処理**

対応するイベントがトリガーされたときにメッセージを送信するUI要素にイベントハンドラーを連結します。 例えば、Chromeベースの送信者アプリケーションの場合、シークイベントは次のように送信されます。

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**受信者メッセージの処理**

受信者アプリから、シークメッセージを処理する方法の例を次に示します。

```js
customMessageBus.onMessage = function (event) { 
    var message = JSON.parse(event.data); 
    switch (message.type) { 
        case "seek":  
            player.seek(parseInt(message.seekTo)); 
            break; 
        //code for handling other events 
        default:  
            break; 
    } 
}; 
```

