---
description: 'null'
seo-description: 'null'
seo-title: ドメインサーバーの設定
title: ドメインサーバーの設定
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ドメインサーバーの設定{#set-up-a-domain-server}

既存のライセンスサーバーのインストール環境でドメインサーバーを設定するには：

1. ディレクトリ [!DNL tomcat/lib] で、ファイルを開 [!DNL flashaccess-refimpl.properties] きます。
1. オプションの `Domain CA certificate` 下で、ドメインCA証明書を入力します。

   次に、この証明書はドメイントークンの受け入れに使用されます。
1. オプションの `Domain CA credential` 下で、詳細を入力 `Domain CA credential certificate (PFX)` します。

   その後、この証明書はドメイン証明書とトークンの署名に使用されます。
1. の値を指定します `DomainServerlURL`。

   この値をに設定すると、ドメイ `NULL`ン認証が成功する場合があります。 ただし、ドメインに参加する際に、参加ドメインのエラーが発生する可能性があります。
