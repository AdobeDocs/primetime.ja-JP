---
title: コンテンツの配信
description: コンテンツの配信
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# コンテンツの配信 {#delivering-content}

Primetime DRM はコンテンツの配信メカニズムに依存しません。ランタイムはネットワークレイヤーを抽象化し、保護されたコンテンツを Primetime DRM サブシステムに提供するだけです。 したがって、HTTP、HTTP Dynamic Streaming、RTMP、RTMPE、HLS などを使用してコンテンツを配信できます。

ただし、プロトコルによっては、保護されたコンテンツのメタデータ ( `DRMContentData`  — 通常、サイドロードされた形で [!DNL .metadata] ファイル ) です。 この DRM メタデータは、 `DRMManager` API（ライセンスのプリフェッチ、DRM 認証、デバイスドメインへの参加など）。 例えば、RTMP/RTMPE プロトコルでは、Flash Media Server(FMS) を通じて FLV と F4V のデータのみをクライアントに配信できます。 このため、クライアントは他の方法でメタデータ blob を取得する必要があります。 この問題を解決する 1 つの方法は、HTTP Web サーバー上でメタデータをホストし、再生されるコンテンツに応じて適切なメタデータを取得するようにクライアントビデオプレーヤーを実装することです。

```
private function getMetadata():void { 
    extrapolated-path-to-metadata = "https://metadatas.mywebserver.com/" + videoname; 
     var urlRequest : URLRequest =  
      new URLRequest(extrapolated-path-to-the-metadata + ".metadata");  
    var urlStream : URLStream = new URLStream();  
    urlStream.addEventListener(Event.COMPLETE, handleMetadata);  
    urlStream.addEventListener(IOErrorEvent.NETWORK_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.IO_ERROR, handleIOError);  
    urlStream.addEventListener(IOErrorEvent.VERIFY_ERROR, handleIOError);  
 
    try { 
        urlStream.load(urlRequest);  
    } catch(se:SecurityError) { 
        videoLog.text += se.toString() + "\n";  
    } catch(e:Error) { 
        videoLog.text += e.toString() + "\n";  
    } 
} 
```
