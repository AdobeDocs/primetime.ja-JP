---
description: Adobe Primetime DRM Server for Protected Streamingは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。
seo-description: Adobe Primetime DRM Server for Protected Streamingは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。
seo-title: Adobe Primetime DRM Server for Protected Streamingについて
title: Adobe Primetime DRM Server for Protected Streamingについて
uuid: 775bef19-6071-428f-80f5-57cae472753c
translation-type: tm+mt
source-git-commit: 68f1318db89cf9422f5969f669c11f3784560db6

---


# Adobe Primetime DRM Server for Protected Streamingについて{#about-adobe-primetime-drm-server-for-protected-streaming}

Adobe Primetime DRM Server for Protected Streamingは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。

保護されたストリーミング用のPrimetime DRMサーバーは、複数のテナントをサポートします。 複数のコンテンツ発行者に代わって、1つのサーバーをホストし、それぞれ独自の設定を行うことができます。 また、サーバーはカスタム認証コンポーネントをサポートしているので、ライセンスが発行される前にカスタムロジックを実行できます。

このサーバは、HTTPストリーミングでの使用を想定しています。 その結果、このサーバー実装は、Primetime DRMで使用可能なすべての機能をサポートしているわけではありません。 例えば、ユーザー認証要求、複数のポリシー、ドメインにバインドされたライセンス、ライセンスのチェーン、同期メッセージはサポートされません。

>[!NOTE]
>
>Adobe Primetime DRMは、以前はAdobe Accessと呼ばれていましたが、それ以前はFlash Accessでした。

