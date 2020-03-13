---
seo-title: DRMErrorEventクラスの使用の概要
title: DRMErrorEventクラスの使用の概要
uuid: cbb9c1a7-3c50-479d-b7e5-63010a696dfa
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# DRMErrorEventクラスの使用 {#using-the-drmerrorevent-class}

Primetimeは、保護されたコン `DRMErrorEvent` テンツを再生しようとして、 [DRM関連のエラーが発生した場合に、Primetimeオブジェクトをディスパッチします](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)。 ユーザーの資格情報が無効な場合、ユーザーが有効な `DRMAuthenticateEvent` 資格情報を入力するか、アプリケーションがそれ以上の試行を拒否するまで、オブジェクトは繰り返しディスパッチします。 アプリケーションは、 [DRM関連のエラーを検出、識別、処理するための他のDRMエラーイベントをリッスンする必要があります](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)。

有効なユーザー資格情報を使用しても、コンテンツのライセンス条項によって、ユーザーが暗号化されたコンテンツを表示できなくなる可能性があります。 例えば、許可されていないアプリケーション（アプリケーションのホワイトリストなど）でコンテンツを表示しようとした場合、ユーザーがアクセスを拒否される可能性があります。 許可されていないアプリケーションとは、ホワイトリストに登録されたアプリケーション署名証明書で署名されていないアプリケーションです。 この場合、オブジェクトが `DRMErrorEvent` ディスパッチされます。

また、コンテンツが破損している場合や、アプリケーションのバージョンがライセンスで指定されたバージョンと一致しない場合にも、エラーイベントが発生する可能性があります。 エラーを処理する適切なメカニズムをアプリケーションが提供する必要があります。

## DRMErrorEventハンドラーの作成 {#create-a-drmerrorevent-handler}

保護されたコンテンツの再生中にエラーが発生した場合にPrimetimeからディスパッチされたエラーイベントを処理するイベントハンドラーを作成します。

通常、アプリケーションでエラーが発生した場合は、任意の数のクリーンアップタスクが実行されます。 次に、エラーをユーザに通知し、問題を解決するためのオプションを提供します。

```
private function drmErrorEventHandler(event:DRMErrorEvent):void {  
    trace(event.toString());  
} 
```
