---
title: カスタム認証/権限付与の概要（オプション）
description: カスタム認証/権限付与の概要（オプション）
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---

# カスタム認証/権限付与の概要（オプション）{#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRM を設定して、独自のバックエンド認証/権限付与サービスに連絡し、以下を決定できます。

* このユーザーはライセンスを取得できますか？
* ライセンスには、どのような権限や制限が必要ですか？

Primetime Cloud DRM には、バックエンドの認証/権限付与サービスの参照実装が含まれています。 デモ用に、このサーバは BEES リクエストに対して「許可」応答を発行しています。 詳しくは、 [!DNL BEESServlet.java] をクリックして、サーバーの動作を変更します。

>[!NOTE]
>
>以前は、この製品は、 *バックエンドの使用権限サーバー* (BEES) の場合、このドキュメント全体およびソースファイル内での BEES への参照。
