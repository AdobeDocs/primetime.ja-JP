---
description: 保護されたストリーミング用のAdobe Primetime DRM サーバーは、Primetime DRM SDK に基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスを Primetime DRM クライアントに発行します。
title: 保護されたストリーミング用のAdobe Primetime DRM サーバーについて
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 保護されたストリーミング用のAdobe Primetime DRM サーバーについて{#about-adobe-primetime-drm-server-for-protected-streaming}

保護されたストリーミング用のAdobe Primetime DRM サーバーは、Primetime DRM SDK に基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスを Primetime DRM クライアントに発行します。

保護されたストリーミング用の Primetime DRM サーバーは、複数のテナントをサポートしています。 複数のコンテンツ発行者に代わって、1 つのサーバーをホストできます。それぞれに独自の設定を持つことができます。 また、サーバーはカスタム認証コンポーネントをサポートしているので、ライセンスが発行される前にカスタムロジックを実行できます。

このサーバは、HTTP ストリーミングでの使用を目的としています。 その結果、このサーバー実装は、Primetime DRM で使用可能なすべての機能をサポートしているわけではありません。 例えば、ユーザー認証要求、複数のポリシー、ドメインバインドライセンス、ライセンスチェーン、同期メッセージはサポートされません。

>[!NOTE]
>
>Adobe Primetime DRM は、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessでした。
