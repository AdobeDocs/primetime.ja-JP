---
seo-title: コンテンツの配信
title: コンテンツの配信
uuid: b277d369-fee3-4a20-9dd8-27b3a8a82a9e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# コンテンツの配信 {#delivering-content}

Primetime DRMはコンテンツの配信メカニズムに依存しません。ランタイムはネットワーク層を抽象化し、保護されたコンテンツをPrimetime DRMサブシステムに提供するだけです。 したがって、コンテンツはHTTP、HTTPダイナミックストリーミング、RTMP、RTMPE、HLSなどを通じて配信できます。

ただし、プロトコルによっては、保護されたコンテンツのメタデータの取得に複雑な問題が発生する場合があります(通常、サイドロードさ `DRMContentData` れたファイルの形式で取得さ [!DNL .metadata] れます)。 このDRMメタデータは、ライセンスのプリフェッチ、DRM認証、 `DRMManager` デバイスドメインへの参加など、任意のAPIを呼び出すために必要です。 例えば、RTMP/RTMPEプロトコルでは、FLVとF4VのデータのみがFlash Media Server(FMS)を介してクライアントに配信できます。 このため、クライアントは他の方法でメタデータBLOBを取得する必要があります。 この問題を解決する1つの方法は、HTTP Webサーバー上でメタデータをホストし、再生中のコンテンツに応じて適切なメタデータを取得するクライアントビデオプレーヤーを実装することです。

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

