---
title: Adobe Access Server for Protected Streaming について
description: Adobe Access Server for Protected Streaming について
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Adobe Access Server for Protected Streaming について{#about-adobe-access-server-for-protected-streaming}

Adobe® Access™ Server for Protected Streaming は、Adobeアクセス SDK に基づくライセンスサーバー実装です。 このサーバは、保護されたコンテンツに対するライセンスをAdobe・アクセス・クライアントに発行します。

Adobe Access Server for Protected Streaming は複数のテナントをサポートしています。つまり、1 台のサーバーを複数のコンテンツ発行者に代わってホストし、それぞれに独自の設定を持たせることができます。 また、サーバーはカスタム認証コンポーネントをサポートしているので、カスタムロジックを実行してからライセンスを発行することができます。

このサーバは、HTTP ストリーミングでの使用を目的としています。 その結果、このサーバー実装は、Adobeアクセスで使用できるすべての機能をサポートしているわけではありません。 例えば、保護されたストリーミング用のAdobe Access Serverは、ユーザー認証要求、複数のポリシー、ドメインバインドライセンス、ライセンスチェーン、同期メッセージをサポートしていません。
