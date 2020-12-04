---
seo-title: カスタム認証/エンタイトルメントの概要（オプション）
title: カスタム認証/エンタイトルメントの概要（オプション）
uuid: 8b5e38a5-562c-4781-ac40-4b3d6cdd97fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
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

