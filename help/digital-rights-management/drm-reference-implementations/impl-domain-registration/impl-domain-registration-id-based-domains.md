---
title: ID ベースのドメイン登録ロジック
description: ID ベースのドメイン登録ロジック
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ID ベースのドメイン登録ロジック{#identity-based-domain-registration-logic}

## ドメイン登録ロジック {#section_149C247458954877AF158B4A09A8526B}

参照実装は、ID ベースのドメイン登録に次のロジックを適用します。

1. 指定されたユーザーに割り当てるドメイン名を決定します。

   ドメイン名 ( `namequalifier:username`) は、認証トークンから抽出されます。 トークンが使用できない場合は、エラーがスローされます。
1. ドメイン名を `DomainServerInfo` 表。

   エントリが見つからない場合は、エントリを挿入します。 デフォルト値は次のとおりです。

   * `authentication required`
   * `max domain membership=5`

   .

1. デバイスがドメインに登録されていることを確認するには：

   1. を参照してください。 `domainname` （内） `UserDomainMembership` テーブル：

      1. 存在するマシン ID ごとに、ID とリクエスト内のマシン ID を比較します。
      1. これが新しいマシンの場合、 `UserDomainMembership` 表。
      1. で一致するレコードを検索 `UserDomainRefCount` 表。
      1. このマシン GUID にエントリが存在しない場合は、レコードを追加します。

   1. 新しいデバイスの場合は、 `Max Membership` の値に達した場合は、エラーを返します。

1. のこのドメインのすべてのドメインキーを検索します `DomainKeys` テーブル：

   1. 次の場合 `DomainServerInfo` キーをロールオーバーし、新しいキーペアを生成する必要があることを示します。
   1. ペアをに保存します。 `DomainKeys` 最も高い既存のキーより 1 つ高いキーバージョンを持つテーブル。
   1. をリセット `Key Rollover Required` 旗を立てる `DomainServerInfo`.

   1. 各ドメインキーに対して、ドメインの資格情報を生成します。

## ドメインの登録解除ロジック {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

参照実装では、ID ベースのドメイン登録解除に対して次のロジックが適用されます。

1. このユーザーに割り当てるドメイン名を決定します。

   ドメイン名はです。 `namequalifier:username`：認証トークンから抽出されます。 トークンがない場合は、エラーを返します。 `DOM_AUTHENTICATION_REQUIRED (503)` が発生します。
1. 要求されたドメイン名を `DomainServerInfo` 表。
1. ドメイン名を `UserDomainMembership` 表。
1. 見つけた各マシン ID と、リクエスト内のマシン ID を比較します。
1. 対応するエントリを `UserDomainRefCount` 表。

   一致するエントリが見つからない場合は、エラーを返します。

1. これがプレビューリクエストでない場合は、 `UserDomainRefCount` 表。
1. マシンの追加のエントリがテーブルにない場合は、次の場所からエントリを削除します。 `UserDomainMembership` をクリックし、 [!DNL Key Rollover Required] ～の旗 `DomainServerInfo` プロパティ。

各ユーザーは少数のマシンを登録できるので、完全なマシン ID と `matches()` マシンをカウントする方法。 ユーザーは異なるブラウザーの複数のAIRアプリケーションやプレーヤーを使用して複数回登録できるので、登録解除もカウントできるように、サーバーでは参照カウントを維持する必要があります。

>[!NOTE]
>
>登録解除は、コンピューター上のすべてのドメイントークンが放棄されるまで完了しません。
