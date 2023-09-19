---
description: TVSDK ベースの送信者アプリから任意のストリームをキャストし、そのストリームを Chromecast 上で Browser TVSDK と共に再生することができます。
title: Browser TVSDK 用のGoogleキャストアプリ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Browser TVSDK 用のGoogleキャストアプリ{#google-cast-app-for-browser-tvsdk}

TVSDK ベースの送信者アプリから任意のストリームをキャストし、そのストリームを Chromecast 上で Browser TVSDK と共に再生することができます。

<!--<a id="section_87CE5D6D46F0439EB6E63A742D6DD9C8"></a>-->

キャスト対応アプリには、次の 2 つのコンポーネントがあります。

* リモートコントロールの役割を果たす送信者アプリです。

  送信者アプリには、スマートフォン、パソコンなどが含まれます。 このアプリは、iOS、Android および Chrome 用のネイティブ SDK を使用して開発できます。
* Chromecast 上で動作し、コンテンツを再生するレシーバーアプリです。

  >[!IMPORTANT]
  >
  >このアプリは、HTML5 のみです。

送信者と受信者は、キャスト SDK を使用してメッセージを渡すことで通信します。

## 基本ワークフロー {#section_FAF680FF29DA4D24A50AC0A2B6402B58}

プロセスの概要を次に示します。

1. 送信者アプリは、受信者アプリとの接続を確立します。
1. 送信者アプリは、受信者アプリにメディアを読み込むためのメッセージを送信します。
1. レシーバーアプリが再生を開始します。
1. 送信者アプリは、再生、一時停止、シーク、早送り、早戻し、巻き戻し、ボリューム変更などの再生制御メッセージを受信者アプリに送信します。
1. 受信者アプリは、これらのメッセージに反応します。

## メッセージの形式 {#section_1624159DD51D4C87B3E5803DEEBCB6B7}

送信者と受信者が理解できるように、メッセージを定義する必要があります。 シークメッセージの例を次に示します。

```js
{ 
"type": "seek", 
"seekTo": 10000 
} 
```

キャスト SDK を通じてシークメッセージなどのカスタムメッセージを送信する場合は、カスタムメッセージ名前空間が必要です。 JavaScript の例を次に示します。

```js
Custom Message Namespace 
var MSG_NAMESPACE = "urn:x-cast:com.adobe.primetime"; 
```

## 接続の確立 {#section_B4D40CABDD3E46FDBE7B5651DFF91653}

>[!IMPORTANT]
>
>接続を確立する際に、ブラウザー TVSDK API は関与しません。

接続を確立するには、送信者と受信者が次のタスクを実行する必要があります。

* 送信者は、次の場所にあるプラットフォームのドキュメントを確認する必要があります。 [送信者のアプリ開発](https://developers.google.com/cast/docs/sender_apps).
* レシーバーは、Cast レシーバー API を使用して、送信者アプリとの接続を確立します。 例：

  ```js
  window.castReceiverManager = cast.receiver.CastReceiverManager.getInstance(); 
  
  window.castReceiverManager.onReady = function (event) { /*handle event*/ }; 
  window.castReceiverManager.onSenderConnected = function (event) { /*handle event*/ }; 
  window.castReceiverManager.onSenderDisconnected = function (event) { /*handle event*/ }; 
  
  var customMessageBus = window.castReceiverManager.getCastMessageBus(MSG_NAMESPACE); 
  customMessageBus.onMessage = function (event) { /*handle messages*/ }; 
  
  window.castReceiverManager.start(); 
  ```

## メッセージの処理 {#section_3E4814546F5946C9B3E7A1AE384B4FF8}

受信者にメッセージを送信するには、送信者のプラットフォームに関するドキュメントを参照してください。

>[!IMPORTANT]
>
>カスタムメッセージの名前空間を含める必要があります。 `MSG_NAMESPACE` を設定します。

レシーバーアプリの場合は、キャストレシーバー API のドキュメントに従います。

**Chrome ベースの送信者メッセージの例**

```js
window.session.sendMessage(MSG_NAMESPACE, message, successCallback, errorCallback); //https://developers.google.com/cast/docs/reference/chrome/chrome.cast.Session#sendMessage
```

**Chrome ベースの送信者イベント処理**

イベントハンドラーを、対応するイベントがトリガーされたときにメッセージを送信する UI 要素にバインドします。 例えば、Chrome ベースの送信者アプリの場合、シークイベントは次のように送信されます。

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
