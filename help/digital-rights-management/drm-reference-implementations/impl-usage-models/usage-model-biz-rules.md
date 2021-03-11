---
title: 使用モデルデモビジネスルール
description: 使用モデルデモビジネスルール
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '251'
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

