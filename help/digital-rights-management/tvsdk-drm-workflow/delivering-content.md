---
seo-title: コンテンツの配信
title: コンテンツの配信
uuid: b277d369-fee3-4a20-9dd8-27b3a8a82a9e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# コンテンツの配信{#delivering-content}

Primetime DRMはコンテンツの配信メカニズムには依存しません。ランタイムはネットワーク層を抽象化し、保護されたコンテンツをPrimetime DRMサブシステムに提供するだけなのです。 したがって、コンテンツはHTTP、HTTP Dynamic Streaming、RTMP、RTMPE、HLSなどを通じて配信できます。

ただし、プロトコルによっては、保護されたコンテンツのメタデータ（`DRMContentData` — 通常はサイドロードされた[!DNL .metadata]ファイルの形式）の取得に、複雑なデータが含まれる場合があります。 このDRMメタデータは、ライセンスのプリフェッチ、DRM認証、デバイスドメインへの参加など、`DRMManager` APIを呼び出すために必要です。 例えば、RTMP/RTMPEプロトコルの場合、FLVとF4VのデータのみがFlash Media Server(FMS)を介してクライアントに配信できます。 このため、クライアントは他の方法でメタデータBLOBを取得する必要があります。 この問題を解決する1つの方法は、HTTP Webサーバー上でメタデータをホストし、再生中のコンテンツに応じて適切なメタデータを取得するようにクライアントビデオプレーヤーを実装することです。

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

