---
description: DRMAuthenticateEvent オブジェクトは、Primetime オブジェクトが、再生前に認証に必要なユーザー資格情報（および認証がまだ実行されていない）を必要とする保護されたコンテンツを再生しようとすると、ディスパッチされます。 DRMAuthenticateEvent ハンドラーは、必要な資格情報（ユーザー名、パスワード、およびタイプ）を収集し、値を.setDRMAuthenticationCredentials() メソッドに渡して検証します。
title: DRMAuthenticateEvent ハンドラーを作成する
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# DRMAuthenticateEvent ハンドラーを作成する{#create-a-drmauthenticateevent-handler}

DRMAuthenticateEvent オブジェクトは、Primetime オブジェクトが、再生前に認証に必要なユーザー資格情報（および認証がまだ実行されていない）を必要とする保護されたコンテンツを再生しようとすると、ディスパッチされます。 DRMAuthenticateEvent ハンドラーは、必要な資格情報（ユーザー名、パスワード、およびタイプ）を収集し、値を.setDRMAuthenticationCredentials() メソッドに渡して検証します。

アプリケーションは、ユーザーの資格情報を取得するためのメカニズムを提供する必要があります。 例えば、ユーザー名とパスワードの値を入力するためのシンプルなユーザーインターフェイスをユーザーに提供できます。 また、認証失敗の繰り返し試行を処理および制限するメカニズムを提供する必要があります。

ハードコードされた一連の認証資格情報を、イベントを発生させた Primetime オブジェクトに渡すイベントハンドラーを作成します。

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

（ビデオを再生し、ビデオストリームへの接続が成功したことを確認するコードは、ここには含まれていません）。
