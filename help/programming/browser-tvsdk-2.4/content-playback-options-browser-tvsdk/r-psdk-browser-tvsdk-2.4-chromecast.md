---
description: TVSDKベースの送信者アプリから任意のストリームをキャストし、ブラウザーTVSDKを使用してChromecastでストリームを再生できます。
seo-description: TVSDKベースの送信者アプリから任意のストリームをキャストし、ブラウザーTVSDKを使用してChromecastでストリームを再生できます。
seo-title: ブラウザーTVSDK用Google Castアプリ
title: ブラウザーTVSDK用Google Castアプリ
uuid: 018143e2-143a-4f88-97c6-4b10a2083f9e
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# ブラウザーTVSDK用Google Castアプリ{#google-cast-app-for-browser-tvsdk}

TVSDKベースの送信者アプリから任意のストリームをキャストし、ブラウザーTVSDKを使用してChromecastでストリームを再生できます。

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

Cast対応アプリには、次の2つのコンポーネントがあります。

* リモートコントロールとして機能する送信者アプリです。

   送信者アプリには、スマートフォン、パソコンなどが含まれます。 アプリは、iOS、Android、Chrome用のネイティブSDKを使用して開発できます。
* 受信側アプリケーション。Chromecastで実行され、コンテンツを再生します。

   >[!IMPORTANT]
   >
   >このアプリはHTML5アプリにのみ使用できます。

送信側と受信側は、キャストSDKを使用してメッセージを渡すことで通信します。

## 基本ワークフロー {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

プロセスの概要を次に示します。

1. 送信者アプリは、受信者アプリとの接続を確立します。
1. 送信者アプリは、受信者アプリにメディアを読み込むためのメッセージを送信します。
1. 受信者アプリは再生を開始します。
1. 送信側のアプリは、再生、一時停止、シーク、早送り、早戻し、巻き戻し、ボリューム変更などの再生制御メッセージを受信側のアプリに送信します。
1. 受信者アプリは、これらのメッセージに反応します。

## メッセージの形式 {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

送信者と受信者が理解できるように、メッセージを定義する必要があります。 シークメッセージの例を次に示します。

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

Cast SDKを介してシークメッセージなどのカスタムメッセージを送信する場合は、カスタムメッセージの名前空間が必要です。 JavaScriptの例を次に示します。

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## 接続の確立 {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>接続を確立する際には、ブラウザーTVSDK APIは関与しません。

接続を確立するには、送信者と受信者が次のタスクを実行する必要があります。

* 送信者は、 [Sender App Developmentでプラットフォームのドキュメントを確認する必要があります](https://developers.google.com/cast/docs/sender_apps)。
* 受信者は、キャスト受信者APIを使用して、送信者アプリとの接続を確立します。 例：

   ```js
   window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
   
   window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
   window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
   
   var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
   customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
   
   window.castReceiverManager.start(); 
   ```

## メッセージ処理 {#section_3E4814546F5946C9B3E7A1AE384B4FF8}

受信者にメッセージを送信するには、送信者のプラットフォームのドキュメントを参照してください。

>[!IMPORTANT]
>
>すべてのメッセージに、カスタムメッセージの名前空間を含 `MSG_NAMESPACE` める必要があります。

受信者アプリの場合は、キャスト受信者APIのドキュメントに従います。

**Chromeベースの送信者メッセージの例**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Chromeベースの送信者イベント処理**

対応するイベントがトリガーされたときにメッセージを送信するUI要素にイベントハンドラーを連結します。 例えば、Chromeベースの送信者アプリの場合、シークイベントは次のように送信されます。

```js
document.getElementById("#seekBar").addEventListener("click", seekEventHandler); 
   
function seekEventHandler(event) { 
    seekMessage = { type: "seek", seekTo: player.currentTime }; //player is an instance of AdobePSDK.MediaPlayer 
    window.session.sendMessage(MSG_NAMESPACE, seekMessage, successCallback, errorCallback); 
} 
```

**受信者のメッセージ処理**

受信者アプリから、シークメッセージの処理方法の例を次に示します。

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

