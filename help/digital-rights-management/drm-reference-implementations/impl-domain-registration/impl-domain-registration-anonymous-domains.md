---
title: 匿名ドメインロジック
description: 匿名ドメインロジック
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# 匿名ドメインロジック{#anonymous-domain-logic}

## ドメイン登録ロジック{#section_C91DCD49D7D44570AF98C2D7B8A283F9}

参照の実装では、匿名ドメインの登録に次のロジックが適用されます。

1. 要求URLからドメイン名を解析します。
1. `DomainServerInfo`テーブルのドメイン名を参照します。
1. エントリが見つからない場合は、テーブルにエントリを挿入します。

   デフォルト値は次のとおりです。

   * `authentication is not required`
   * `no membership maximum`

   要求されたドメインに認証が必要な場合は、有効な認証トークンが要求内にあることを確認します。 データベースで認証名前空間が指定されている場合、トークンは指定された認証名前空間と一致する必要があります。
1. 認証が必要で、有効な認証トークンが使用できない場合は、エラー`DOM_AUTHENTICATION_REQUIRED (503)`を返します。
1. デバイスがドメインに登録されているかどうかを確認します。

   1. `DomainMembership`テーブルのドメイン名を参照します。
   1. 検索したマシンGUIDと、要求内のマシンGUIDを比較します。
   1. これが新しいマシンの場合は、`DomainMembership`テーブルにエントリを追加します。
   1. 新しいデバイスで`Max Membership`値に達した場合は、エラー`DOM_LIMIT_REACHED (502)`を返します。

1. `DomainKeys`テーブルで、このドメインのすべてのドメインキーを検索します。

   1. `DomainServerInfo`がキーをロールオーバーする必要があることを示している場合は、新しいキーペアを生成します。
   1. 既存のキーの上位より1つ大きいキーバージョンのキーを`DomainKeys`テーブルに保存します。
   1. `DomainServerInfo`の`Key Rollover Required`フラグをリセットします。

   1. 各ドメインキーに対して、ドメイン秘密鍵証明書を生成します。

## ドメイン登録解除ロジック{#section_C968BBFCBFAB4510A903D169F38C9FCE}

参照の実装では、匿名ドメインの登録解除に次のロジックが適用されます。

1. 要求URLからドメイン名を解析します。
1. `DomainServerInfo`テーブルで、要求されたドメイン名を検索します。
1. 要求されたドメインに認証が必要な場合は、有効な認証トークンが要求内にあることを確認します。

   また、トークンは、データベースで指定されているAuth名前空間と一致する必要があります。
1. `DomainMembership`テーブルのドメイン名とマシンGUIDを参照します。

   一致するエントリが見つからない場合は、エラー`DEREG_DENIED (401)`を返します。

1. これがプレビューリクエストでない場合は、`DomainMembership`からエントリを削除し、`DomainServerInfo`に`Key Rollover Required`フラグを設定します。

多数のマシンがドメインに加入している可能性があるので、マシンIDを単純に一致させることはできません。 代わりに、個別化の際にマシンに割り当てられるランダムなマシンGUIDが適用されます。
