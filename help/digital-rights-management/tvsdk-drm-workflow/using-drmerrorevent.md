---
seo-title: DRMErrorEventクラスの使用の概要
title: DRMErrorEventクラスの使用の概要
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# DRMErrorEventクラスの使用 {#using-the-drmerrorevent-class}

Primetimeは、保護されたコンテンツを再生しようとするPrimetimeオブジェクトが `DRMErrorEvent` DRM関連のエラーを検出すると、 [オブジェクトをディスパッチします](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)。 ユーザーの資格情報が無効な場合、 `DRMAuthenticateEvent` オブジェクトは、ユーザーが有効な資格情報を入力するか、アプリケーションがそれ以上の試行を拒否するまで、繰り返しディスパッチします。 アプリケーションは、 [DRM関連のエラーを検出、識別、処理するための他のDRMエラーイベントをリッスンする必要があります](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)。

有効なユーザー資格情報を持っていても、コンテンツのライセンス条項によって、ユーザーが暗号化されたコンテンツを表示できなくなる場合があります。 例えば、許可されていないアプリケーション（アプリケーションの許可リストなど）でコンテンツを表示しようとした場合、ユーザーがアクセスを拒否される場合があります。 許可されていないアプリケーションとは、リストに記載されたアプリケーション署名証明書を使用して署名されていないアプリケーションのことです。 この場合、 `DRMErrorEvent` オブジェクトがディスパッチされます。

コンテンツが破損している場合や、アプリケーションのバージョンがライセンスで指定されたバージョンと一致しない場合は、エラーイベントを実行することもできます。 アプリケーションは、エラーを処理するための適切なメカニズムを提供する必要があります。

## DRMErrorEventハンドラーの作成 {#create-a-drmerrorevent-handler}

保護されたコンテンツの再生を試みているときにエラーが発生した場合にPrimetimeからディスパッチされるエラーイベントを処理するイベントハンドラーを作成します。

通常、アプリケーションはエラーを検出すると、任意の数のクリーンアップタスクを実行します。 その後、エラーをユーザに通知し、問題を解決するためのオプションを提供します。

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
