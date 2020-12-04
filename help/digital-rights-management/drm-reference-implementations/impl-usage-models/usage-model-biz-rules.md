---
description: 'null'
seo-description: 'null'
seo-title: 使用モデルデモビジネスルール
title: 使用モデルデモビジネスルール
uuid: c55f85be-5ecb-4a78-b47d-7001ec207d3a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# 使用モデルデモビジネスルール{#usage-model-demo-business-rules}

ユーザーがライセンスを要求すると、参照実装サーバーはクライアントが送信したメタデータを調べ、`RI_UsageModelDemo`プロパティを使用してコンテンツがパッケージ化されたかどうかを判断します。 その場合、サーバーは次のビジネスルールを適用します。

* DRMポリシーの1つで認証が必要な場合：

   * リクエストに有効な認証トークンが含まれている場合は、Customerデータベーステーブルでユーザー名を検索します。

      ユーザーの名前が見つからない場合は、次のタスクを入力します。

      * `Customer.IsSubscriber`プロパティを`true`に設定する場合は、*`Subscription`*&#x200B;使用モデルのライセンスを生成し、ユーザーに送信する必要があります。

      * `CustomerAuthorization`データベーステーブルで、ユーザー名とコンテンツIDのレコードを検索します。

      ユーザーのレコードが見つかった場合は、次のタスクを実行します。

      * `CustomerAuthorization.UsageType`プロパティが`DTO`に設定されている場合は、DTO使用モデルのライセンスを生成し、ユーザーに送信します。

      * `CustomerAuthorization.UsageType`プロパティが`VOD`に設定されている場合は、VOD使用モデルのライセンスを生成し、ユーザーに送信します。

      匿名アクセスを許可するDRMポリシーが1つもない場合は、次のタスクを実行します。

      * 要求内に有効な認証トークンがない場合は、「認証が必要です」というエラーを返す必要があります。
      * それ以外の場合は、「認証されていません」というエラーが返されます。



* DRMポリシーの1つで匿名アクセスが許可されている場合は、広告が出資した使用モデルのライセンスを生成し、ユーザーに送信します。

