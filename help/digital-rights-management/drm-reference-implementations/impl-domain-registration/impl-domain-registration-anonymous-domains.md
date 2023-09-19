---
title: 匿名ドメインロジック
description: 匿名ドメインロジック
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 匿名ドメインロジック{#anonymous-domain-logic}

## ドメイン登録ロジック {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

参照実装では、匿名ドメイン登録に対して次のロジックが適用されます。

1. 要求 URL からドメイン名を解析します。
1. ドメイン名を `DomainServerInfo` 表。
1. エントリが見つからない場合は、テーブルにエントリを挿入します。

   デフォルト値は次のとおりです。

   * `authentication is not required`
   * `no membership maximum`

   リクエストされたドメインに認証が必要な場合は、有効な認証トークンがリクエストに含まれていることを確認します。 データベースで Auth 名前空間が指定されている場合、トークンは指定された Auth 名前空間と一致する必要があります。
1. 認証が必要で、有効な認証トークンが使用できない場合は、エラーを返します。 `DOM_AUTHENTICATION_REQUIRED (503)`.
1. デバイスがドメインに登録されているかどうかを確認します。

   1. ドメイン名を `DomainMembership` 表。
   1. 探したマシン GUID と、リクエスト内のマシン GUID を比較します。
   1. これが新しいマシンの場合、 `DomainMembership` 表。
   1. 新しいデバイスで、 `Max Membership` 値に達しました。エラーを返します `DOM_LIMIT_REACHED (502)`.

1. のこのドメインのすべてのドメインキーを検索します `DomainKeys` テーブル：

   1. 次の場合 `DomainServerInfo` は、キーをロールオーバーする必要があることを示し、新しいキーペアを生成します。
   1. キーペアを `DomainKeys` 最も大きい既存のキーより 1 つ大きい数値を持つキーバージョンのテーブル。
   1. をリセット `Key Rollover Required` 旗を立てる `DomainServerInfo`.

   1. 各ドメインキーに対して、ドメインの資格情報を生成します。

## ドメインの登録解除ロジック {#section_C968BBFCBFAB4510A903D169F38C9FCE}

この参照実装では、匿名ドメインの登録解除に対して次のロジックが適用されます。

1. 要求 URL からドメイン名を解析します。
1. 要求されたドメイン名を `DomainServerInfo` 表。
1. リクエストされたドメインに認証が必要な場合は、有効な認証トークンがリクエストに含まれていることを確認します。

   トークンは、データベースで指定されている Auth 名前空間とも一致する必要があります。
1. のドメイン名とマシン GUID を検索します。 `DomainMembership` 表。

   一致するエントリが見つからない場合は、エラーを返します。 `DEREG_DENIED (401)`.

1. これがプレビューリクエストでない場合は、 `DomainMembership`、および `DomainServerInfo`を設定し、 `Key Rollover Required` フラグ。

多数のマシンがドメインに参加する可能性があるので、単にマシン ID を照合することはできません。 代わりに、個別化時にマシンに割り当てられるランダムマシン GUID が適用されます。
