---
title: DRMErrorEventクラスの使用の概要
description: DRMErrorEventクラスの使用の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---


# DRMErrorEventクラスの概要{#using-the-drmerrorevent-class-overview}の使用

Primetimeは、保護されたコンテンツを再生しようとしているPrimetimeオブジェクトが[DRM関連のエラー](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)を検出すると、`DRMErrorEvent`オブジェクトをディスパッチします。 ユーザーの資格情報が無効な場合、`DRMAuthenticateEvent`オブジェクトは、ユーザーが有効な資格情報を入力するか、アプリケーションがそれ以上の試行を拒否するまで、繰り返しディスパッチします。 アプリケーションは、[DRM関連のエラー](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)を検出、識別、処理するための、他のDRMエラーイベントをリッスンする必要があります。

有効なユーザー資格情報を持っていても、コンテンツのライセンス条項によって、ユーザーが暗号化されたコンテンツを表示できなくなる場合があります。 例えば、許可されていないアプリケーション（アプリケーションの許可リストなど）でコンテンツを表示しようとした場合、ユーザーがアクセスを拒否される場合があります。 許可されていないアプリケーションとは、リストに記載されたアプリケーション署名証明書を使用して署名されていないアプリケーションです。 この場合、`DRMErrorEvent`オブジェクトがディスパッチされます。

コンテンツが破損している場合や、アプリケーションのバージョンがライセンスで指定されたバージョンと一致しない場合は、エラーイベントを実行することもできます。 アプリケーションは、エラーを処理するための適切なメカニズムを提供する必要があります。
