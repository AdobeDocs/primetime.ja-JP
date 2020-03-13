---
description: 'null'
seo-description: 'null'
seo-title: Protected Streaming用のAdobe Access Serverについて
title: Protected Streaming用のAdobe Access Serverについて
uuid: a02a98ad-bb1a-4c1f-931d-412945561a8c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Protected Streaming用のAdobe Access Serverについて{#about-adobe-access-server-for-protected-streaming}

Adobe® Access™ Server for Protected Streamingは、Adobe Access SDKに基づくライセンスサーバー実装です。 このサーバーは、保護されたコンテンツのライセンスをAdobe Accessクライアントに発行します。

保護されたストリーミング用のAdobe Access Serverは複数のテナントをサポートしています。つまり、1つのサーバーを複数のコンテンツ発行者の代わりにホストし、それぞれに独自の設定を指定できます。 また、サーバーはカスタム認証コンポーネントをサポートしているので、ライセンスを発行する前にカスタムロジックを実行できます。

このサーバは、HTTPストリーミングでの使用を想定しています。 その結果、このサーバーの実装は、Adobe Accessで使用可能なすべての機能をサポートしているわけではありません。 例えば、Protected Streaming用のAdobe Access Serverは、ユーザー認証要求、複数のポリシー、ドメインバインドライセンス、ライセンスチェーン、同期メッセージをサポートしていません。
