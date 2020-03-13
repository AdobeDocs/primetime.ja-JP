---
description: 'null'
seo-description: 'null'
seo-title: IDベースのドメイン登録ロジック
title: IDベースのドメイン登録ロジック
uuid: bc13f7c2-9a20-4f80-b96f-05f7a0fcc343
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# IDベースのドメイン登録ロジック{#identity-based-domain-registration-logic}

## ドメイン登録ロジック {#section_149C247458954877AF158B4A09A8526B}

参照実装では、IDベースのドメイン登録に次のロジックが適用されます。

1. 指定したユーザーに割り当てるドメイン名を決定します。

   ドメイン名( `namequalifier:username`)は認証トークンから抽出されます。 トークンが使用できない場合は、エラーが発生します。
1. 表でドメイン名を検索し `DomainServerInfo` ます。

   エントリが見つからない場合は、エントリを挿入します。 デフォルト値は次のとおりです。

   * `authentication required`
   * `max domain membership=5`
   .

1. デバイスがドメインに登録されていることを確認するには：

   1. 表の中のを `domainname` 調べま `UserDomainMembership` す。

      1. 見つかった各マシンIDについて、IDとリクエスト内のマシンIDを比較します。
      1. これが新しいマシンの場合は、テーブルにエントリを追加し `UserDomainMembership` ます。
      1. テーブル内の一致するレコードを検索 `UserDomainRefCount` します。
      1. このマシンGUIDのエントリが存在しない場合は、レコードを追加します。
   1. 新しいデバイスで、値に達した場合は、 `Max Membership` エラーを返します。


1. 表内のこのドメインのすべてのドメインキーを検索し `DomainKeys` ます。

   1. キーを `DomainServerInfo` ロールオーバーする必要があることを示す場合は、新しいキーペアを生成します。
   1. 既存の最も高いキーよ `DomainKeys` りも1つ高いキーバージョンを持つペアをテーブルに保存します。
   1. でフラグをリセ `Key Rollover Required` ットしま `DomainServerInfo`す。

   1. 各ドメインキーに対して、ドメイン秘密鍵証明書を生成します。

## ドメイン登録解除ロジック {#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

参照実装では、IDベースのドメインの登録解除に次のロジックが適用されます。

1. このユーザーに割り当てるドメイン名を決定します。

   ドメイン名は、認 `namequalifier:username`証トークンから抽出されます。 使用できるトークンがない場合は、エラーが返さ `DOM_AUTHENTICATION_REQUIRED (503)` れます。
1. 表で要求されたドメイン名を検索し `DomainServerInfo` ます。
1. 表でドメイン名を検索し `UserDomainMembership` ます。
1. 検索した各マシンIDを、リクエスト内のマシンIDと比較します。
1. テーブル内の対応するエントリを探 `UserDomainRefCount` します。

   一致するエントリが見つからない場合は、エラーを返します。

1. プレビューリクエストでない場合は、テーブルからエントリを削除し `UserDomainRefCount` ます。
1. マシンのテーブルに追加のエントリがない場合は、からエントリを削除し、プ `UserDomainMembership` ロパティにフ [!DNL Key Rollover Required] ラグを設定し `DomainServerInfo` ます。

各ユーザーは少数のマシンを登録できるので、マシンID全体とその方法を使用してマシンをカウ `matches()` ントすることができます。 ユーザーは複数のAIRアプリケーションまたは異なるブラウザーのプレーヤーを使用して複数回登録できるので、登録解除もカウントできるように、サーバーは参照カウントを維持する必要があります。

>[!NOTE]
>
>マシン上のドメイントークンがすべて放棄されるまで、登録解除は完了しません。

