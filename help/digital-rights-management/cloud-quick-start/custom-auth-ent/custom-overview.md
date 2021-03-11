---
title: カスタム認証/エンタイトルメントの概要（オプション）
description: カスタム認証/エンタイトルメントの概要（オプション）
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 0%

---


# カスタム認証/エンタイトルメントの概要（オプション）{#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRMは、独自のバックエンド認証/エンタイトルメントサービスに到達するように設定して、次の項目を決定できます。

* このユーザーはライセンスの取得を許可されていますか？
* ライセンスに含める権利/制限

Primetime Cloud DRMには、バックエンドの認証/エンタイトルメントサービスのリファレンス実装が含まれています。 このサーバーは、デモ目的で、BEESリクエストに対して「許可」応答を発行しています。 [!DNL BEESServlet.java]を参照して、サーバの動作を変更してください。

>[!NOTE]
>
>以前は、これは&#x200B;*Back End Entitlement Server* (BEES)と呼ばれる別の製品でした。したがって、このドキュメント全体およびソースファイル内でBEESに対する参照が行われていました。

