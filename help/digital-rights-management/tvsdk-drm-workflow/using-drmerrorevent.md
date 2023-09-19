---
title: DRMErrorEvent クラスの使用：概要
description: DRMErrorEvent クラスの使用：概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# DRMErrorEvent クラスの使用 {#using-the-drmerrorevent-class}

Primetime が `DRMErrorEvent` オブジェクトは、保護されたコンテンツを再生しようとして、Primetime オブジェクトに対して [DRM 関連のエラー](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages). ユーザーの資格情報が無効な場合、 `DRMAuthenticateEvent` オブジェクトは、ユーザーが有効な資格情報を入力するか、アプリケーションがそれ以上の試行を拒否するまで、繰り返しディスパッチされます。 アプリケーションは、その他の DRM エラーイベントをリッスンして、 [DRM 関連のエラー](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages).

有効なユーザー資格情報を持っていても、コンテンツのライセンス条件によって、ユーザーが暗号化されたコンテンツを表示できなくなる場合があります。 例えば、ユーザーが権限のないアプリケーション（アプリケーションの許可リストへの登録など）でコンテンツを表示しようとした場合、アクセスを拒否できます。 許可されていないアプリケーションとは、許可リストに登録されたアプリケーション署名証明書を使用して署名されていないアプリケーションです。 この場合、 `DRMErrorEvent` オブジェクトがディスパッチされます。

コンテンツが破損している場合や、アプリケーションのバージョンがライセンスで指定されたバージョンと一致しない場合にも、エラーイベントを発生させることができます。 アプリケーションは、エラーを処理するための適切なメカニズムを提供する必要があります。

## DRMErrorEvent ハンドラーを作成する {#create-a-drmerrorevent-handler}

保護されたコンテンツの再生中にエラーが発生した場合に Primetime からディスパッチされるエラーイベントを処理するイベントハンドラーを作成します。

通常、アプリケーションでエラーが発生した場合は、任意の数のクリーンアップタスクを実行します。 その後、エラーをユーザーに通知し、問題を解決するためのオプションを提供します。

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
