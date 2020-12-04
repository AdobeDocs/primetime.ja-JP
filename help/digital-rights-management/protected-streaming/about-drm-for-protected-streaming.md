---
description: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。
seo-description: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。
seo-title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーについて
title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーについて
uuid: 775bef19-6071-428f-80f5-57cae472753c
translation-type: tm+mt
source-git-commit: 68f1318db89cf9422f5969f669c11f3784560db6
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# 保護されたストリーミング用のAdobe PrimetimeDRMサーバーについて{#about-adobe-primetime-drm-server-for-protected-streaming}

保護されたストリーミング用のAdobe PrimetimeDRMサーバーは、Primetime DRM SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをPrimetime DRMクライアントに発行します。

保護されたストリーミング用のPrimetime DRMサーバーは、複数のテナントをサポートします。 複数のコンテンツ発行者に代わって、それぞれ独自の設定を持つ単一のサーバーをホストできます。 また、サーバーはカスタム認証コンポーネントをサポートするので、ライセンスが発行される前にカスタムロジックを実行できます。

このサーバは、HTTPストリーミングでの使用を想定しています。 その結果、このサーバーの実装は、Primetime DRMで使用可能なすべての機能をサポートしているわけではありません。 例えば、ユーザー認証要求、複数のポリシー、ドメインバインドライセンス、ライセンスチェーン、同期メッセージはサポートされません。

>[!NOTE]
>
>Adobe PrimetimeDRMは、以前はAdobeアクセスと呼ばれていましたが、それ以前はFlash Accessと呼ばれていました。

