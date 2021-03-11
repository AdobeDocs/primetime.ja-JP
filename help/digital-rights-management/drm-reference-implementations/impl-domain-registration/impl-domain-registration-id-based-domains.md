---
title: IDベースのドメイン登録ロジック
description: IDベースのドメイン登録ロジック
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# IDベースのドメイン登録ロジック{#identity-based-domain-registration-logic}

## ドメイン登録ロジック{#section_149C247458954877AF158B4A09A8526B}

参照の実装では、IDベースのドメイン登録に次のロジックが適用されます。

1. 指定したユーザーに割り当てるドメイン名を決定します。

   ドメイン名(`namequalifier:username`)は認証トークンから抽出されます。 トークンが使用できない場合は、エラーが発生します。
1. `DomainServerInfo`テーブルのドメイン名を参照します。

   エントリが見つからない場合は、エントリを挿入します。 デフォルト値は次のとおりです。

   * `authentication required`
   * `max domain membership=5`

   .

1. デバイスがドメインに登録されていることを確認するには：

   1. `UserDomainMembership`テーブルの`domainname`を参照します。

      1. 検索されるマシンIDごとに、IDとリクエスト内のマシンIDを比較します。
      1. これが新しいマシンの場合は、`UserDomainMembership`テーブルにエントリを追加します。
      1. `UserDomainRefCount`テーブルで一致するレコードを検索します。
      1. このマシンのGUIDにエントリが存在しない場合は、レコードを追加します。
   1. 新しいデバイスで、`Max Membership`値に達した場合は、エラーを返します。


1. `DomainKeys`テーブルで、このドメインのすべてのドメインキーを検索します。

   1. `DomainServerInfo`がキーをロールオーバーする必要があると示した場合は、新しいキーペアを生成します。
   1. ペアを`DomainKeys`テーブルに保存し、既存の最も高いキーよりも1つ高いキーバージョンを使用します。
   1. `DomainServerInfo`の`Key Rollover Required`フラグをリセットします。

   1. 各ドメインキーに対して、ドメイン秘密鍵証明書を生成します。

## ドメイン登録解除ロジック{#section_78AFA63D8F744BE6BCA10A51B4FCBA22}

このリファレンスの実装では、IDベースのドメインの登録解除に次のロジックが適用されます。

1. このユーザーに割り当てるドメイン名を決定します。

   ドメイン名は`namequalifier:username`で、認証トークンから抽出されます。 利用できるトークンがない場合は、エラー`DOM_AUTHENTICATION_REQUIRED (503)`が返されます。
1. `DomainServerInfo`テーブルで、要求されたドメイン名を検索します。
1. `UserDomainMembership`テーブルのドメイン名を参照します。
1. 検索した各マシンIDと、リクエスト内のマシンIDを比較します。
1. `UserDomainRefCount`テーブル内の対応するエントリを探します。

   一致するエントリが見つからない場合は、エラーを返します。

1. プレビューリクエストでない場合は、`UserDomainRefCount`テーブルからエントリを削除します。
1. マシンに対してそのテーブルに追加のエントリがない場合は、`UserDomainMembership`からエントリを削除し、`DomainServerInfo`プロパティに[!DNL Key Rollover Required]フラグを設定します。

各ユーザーは少数のマシンを登録できるので、マシンID全体と`matches()`メソッドを使ってマシンをカウントできます。 ユーザーは複数のAIRアプリケーションまたは異なるブラウザーのプレーヤーを使用して複数回登録できるので、登録解除もカウントできるように、サーバーは参照カウントを維持する必要があります。

>[!NOTE]
>
>登録解除は、マシン上のすべてのドメイントークンが放棄されるまで完了しません。

