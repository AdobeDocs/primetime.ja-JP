---
description: 'null'
seo-description: 'null'
seo-title: 匿名ドメインロジック
title: 匿名ドメインロジック
uuid: bd0e8e51-27dc-4ccf-b285-a80c2ab9e260
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 匿名ドメインロジック{#anonymous-domain-logic}

## ドメイン登録ロジック {#section_C91DCD49D7D44570AF98C2D7B8A283F9}

参照の実装では、匿名ドメインの登録に次のロジックが適用されます。

1. 要求URLからドメイン名を解析します。
1. 表でドメイン名を検索し `DomainServerInfo` ます。
1. エントリが見つからない場合は、テーブルにエントリを挿入します。

   デフォルト値は次のとおりです。

   * `authentication is not required`
   * `no membership maximum`
   要求されたドメインに認証が必要な場合は、有効な認証トークンが要求に含まれていることを確認します。 データベースで認証名前空間が指定されている場合、トークンは指定された認証名前空間と一致する必要があります。
1. 認証が必要で、有効な認証トークンが使用できない場合は、エラーを返しま `DOM_AUTHENTICATION_REQUIRED (503)`す。
1. デバイスがドメインに登録されているかどうかを確認します。

   1. 表でドメイン名を検索し `DomainMembership` ます。
   1. 検索したコンピューターGUIDと、要求内のコンピューターGUIDを比較します。
   1. これが新しいマシンの場合は、テーブルにエントリを追加し `DomainMembership` ます。
   1. 新しいデバイスで、値に達し `Max Membership` た場合は、エラーを返します `DOM_LIMIT_REACHED (502)`。

1. 表内のこのドメインのすべてのドメインキーを検索し `DomainKeys` ます。

   1. キーを `DomainServerInfo` ロールオーバーする必要がある場合は、新しいキーペアを生成します。
   1. 既存のキーの中で最も大き `DomainKeys` い方の1つの番号を持つキーバージョンを使用して、テーブルにキーペアを保存します。
   1. でフラグをリセ `Key Rollover Required` ットしま `DomainServerInfo`す。

   1. 各ドメインキーに対して、ドメイン秘密鍵証明書を生成します。

## ドメイン登録解除ロジック {#section_C968BBFCBFAB4510A903D169F38C9FCE}

参照の実装では、匿名ドメインの登録解除に次のロジックが適用されます。

1. 要求URLからドメイン名を解析します。
1. 表で要求されたドメイン名を検索し `DomainServerInfo` ます。
1. 要求されたドメインに認証が必要な場合は、有効な認証トークンが要求に含まれていることを確認します。

   また、トークンは、データベースで指定されているAuth名前空間と一致する必要があります。
1. 表内のドメイン名とマシンGUIDを検索し `DomainMembership` ます。

   一致するエントリが見つからない場合は、エラーを返しま `DEREG_DENIED (401)`す。

1. これがプレビュー要求でない場合は、からエントリを削 `DomainMembership`除し、でフ `DomainServerInfo`ラグを設定し `Key Rollover Required` ます。

多数のマシンがドメインに加入している可能性があるので、マシンIDを単純に一致させることはできません。 代わりに、個別化の際にマシンに割り当てられるランダムなマシンGUIDが適用されます。
