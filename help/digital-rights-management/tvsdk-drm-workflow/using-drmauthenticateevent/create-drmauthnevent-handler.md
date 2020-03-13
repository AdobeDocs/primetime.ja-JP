---
description: DRMAuthenticateEventオブジェクトは、再生前に認証用のユーザー資格情報を必要とする保護されたコンテンツをPrimetimeオブジェクトが再生しようとするとディスパッチされます（認証はまだ実行されていません）。 DRMAuthenticateEventハンドラーは、必要な資格情報（ユーザー名、パスワードおよびタイプ）を収集し、検証のために.setDRMAuthenticationCredentials()メソッドに値を渡す役割を持ちます。
seo-description: DRMAuthenticateEventオブジェクトは、再生前に認証用のユーザー資格情報を必要とする保護されたコンテンツをPrimetimeオブジェクトが再生しようとするとディスパッチされます（認証はまだ実行されていません）。 DRMAuthenticateEventハンドラーは、必要な資格情報（ユーザー名、パスワードおよびタイプ）を収集し、検証のために.setDRMAuthenticationCredentials()メソッドに値を渡す役割を持ちます。
seo-title: DRMAuthenticateEventハンドラーの作成
title: DRMAuthenticateEventハンドラーの作成
uuid: 58330691-d0b5-46bd-9b1d-8dc597580d31
translation-type: tm+mt
source-git-commit: 5749142d42f7d7b36c96592955d1f71f6a7956fc

---


# DRMAuthenticateEventハンドラーの作成{#create-a-drmauthenticateevent-handler}

DRMAuthenticateEventオブジェクトは、再生前に認証用のユーザー資格情報を必要とする保護されたコンテンツをPrimetimeオブジェクトが再生しようとするとディスパッチされます（認証はまだ実行されていません）。 DRMAuthenticateEventハンドラーは、必要な資格情報（ユーザー名、パスワードおよびタイプ）を収集し、検証のために.setDRMAuthenticationCredentials()メソッドに値を渡す役割を持ちます。

アプリケーションは、ユーザーの資格情報を取得するためのメカニズムを提供する必要があります。 例えば、ユーザー名とパスワードの値を入力するためのシンプルなユーザーインターフェイスをユーザーに提供できます。 また、認証失敗の繰り返しを処理および制限するメカニズムを提供する必要があります。

ハードコードされた認証資格情報のセットを、イベントの発生元のPrimetimeオブジェクトに渡すイベントハンドラーを作成します。

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
