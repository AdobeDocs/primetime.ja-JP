---
description: 'null'
seo-description: 'null'
seo-title: Protected StreamingのAdobe Access Serverについて
title: Protected StreamingのAdobe Access Serverについて
uuid: a02a98ad-bb1a-4c1f-931d-412945561a8c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---


# 保護されたストリーミングのAdobe Access Serverについて{#about-adobe-access-server-for-protected-streaming}

Adobe® Access™ Server for Protected Streamingは、AdobeアクセスSDKに基づくライセンスサーバの実装です。 このサーバーは、保護されたコンテンツのライセンスをAdobeアクセスクライアントに発行します。

保護ストリーミング用のAdobe Access Serverでは、複数のテナントがサポートされています。つまり、1台のサーバーを複数のコンテンツ発行者の代わりにホストでき、それぞれに独自の設定があります。 また、サーバーはカスタム認証コンポーネントをサポートしているので、ライセンスを発行する前にカスタムロジックを実行できます。

このサーバは、HTTPストリーミングでの使用を想定しています。 その結果、このAdobeの実装は、サーバーアクセスで使用可能なすべての機能をサポートしているわけではありません。 例えば、保護されたストリーミング用のAdobe Access Serverは、ユーザー認証要求、複数のポリシー、ドメインバインドライセンス、ライセンスチェーン、同期メッセージをサポートしていません。
