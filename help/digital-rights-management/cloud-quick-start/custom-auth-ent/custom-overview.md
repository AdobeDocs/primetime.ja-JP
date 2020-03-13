---
seo-title: カスタム認証/エンタイトルメントの概要（オプション）
title: カスタム認証/エンタイトルメントの概要（オプション）
uuid: 8b5e38a5-562c-4781-ac40-4b3d6cdd97fe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# カスタム認証/エンタイトルメントの概要（オプション）{#custom-authentication-entitlement-overview-optional}

Primetime Cloud DRMは、独自のバックエンド認証/エンタイトルメントサービスに到達するように設定し、次の項目を決定できます。

* このユーザーはライセンスの取得を許可されていますか？
* ライセンスに含める権利/制限

Primetime Cloud DRMには、バックエンドの認証/エンタイトルメントサービスのリファレンス実装が含まれています。 デモ用に、このサーバはBEES要求に対して「許可」応答を発行しています。 サーバの動 [!DNL BEESServlet.java] 作を変更するにはを参照してください。

>[!NOTE]
>
>以前は、これは *Back End Entitlement Server* (BEES)と呼ばれる別の製品で、このドキュメント全体およびソースファイル内のBEESへの参照です。

