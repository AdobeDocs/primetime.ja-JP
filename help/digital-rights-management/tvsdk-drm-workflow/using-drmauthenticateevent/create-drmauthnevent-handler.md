---
description: DRMAuthenticateEventオブジェクトは、再生前に認証用のユーザー資格情報を必要とする保護されたコンテンツをPrimetimeオブジェクトが再生しようとするとき（ただし、認証はまだ実行されていません）にディスパッチされます。 DRMAuthenticateEventハンドラーは、必要な資格情報（ユーザー名、パスワード、およびタイプ）を収集し、検証のために.setDRMAuthenticationCredentials()メソッドに値を渡す役割を持ちます。
title: DRMAuthenticateEventハンドラーの作成
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# DRMAuthenticateEventハンドラーの作成{#create-a-drmauthenticateevent-handler}

DRMAuthenticateEventオブジェクトは、再生前に認証用のユーザー資格情報を必要とする保護されたコンテンツをPrimetimeオブジェクトが再生しようとするとき（ただし、認証はまだ実行されていません）にディスパッチされます。 DRMAuthenticateEventハンドラーは、必要な資格情報（ユーザー名、パスワード、およびタイプ）を収集し、検証のために.setDRMAuthenticationCredentials()メソッドに値を渡す役割を持ちます。

アプリケーションは、ユーザーの資格情報を取得するためのメカニズムを提供する必要があります。 例えば、ユーザー名とパスワードの値を入力する単純なユーザーインターフェイスをユーザーに提供できます。 また、認証失敗の繰り返しを処理および制限するメカニズムを提供する必要があります。

ハードコードされた認証資格情報のセットを、イベントを発生させたPrimetimeオブジェクトに渡すイベントハンドラーを作成します。

```
var connection:NetConnection = new NetConnection();  
connection.connect(null);  
var videoStream:Primetime = new Primetime(connection);  
 
videoStream.addEventListener( 
  DRMAuthenticateEvent.DRM_AUTHENTICATE,  
  drmAuthenticateEventHandler)  
  private function drmAuthenticateEventHandler(event:DRMAuthenticateEvent):void {  
    videoStream.setDRMAuthenticationCredentials("administrator", "password", "drm");  
} 
```

（ビデオを再生し、ビデオストリームへの接続が成功したことを確認するコードは、ここには含まれません）。
