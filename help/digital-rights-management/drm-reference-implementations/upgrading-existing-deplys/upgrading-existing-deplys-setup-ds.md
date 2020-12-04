---
description: 'null'
seo-description: 'null'
seo-title: ドメインサーバーのセットアップ
title: ドメインサーバーのセットアップ
uuid: bf85305e-9a00-4bc0-ba36-c870979456e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# ドメインサーバーのセットアップ{#set-up-a-domain-server}

既存のライセンスサーバーのインストールにドメインサーバーを設定するには：

1. [!DNL tomcat/lib]ディレクトリで、[!DNL flashaccess-refimpl.properties]ファイルを開きます。
1. `Domain CA certificate`オプションの下で、ドメインCA証明書を入力します。

   この証明書は、次に、ドメイントークンの受け入れに使用されます。
1. `Domain CA credential`オプションの下で、`Domain CA credential certificate (PFX)`の詳細を入力します。

   その後、この証明書をドメインの証明書とトークンの署名に使用します。
1. `DomainServerlURL`の値を指定します。

   この値を`NULL`に設定すると、ドメイン認証が成功する場合があります。 ただし、ドメインに参加している間に、参加ドメインのエラーが発生する場合があります。
