---
title: ドメインサーバーのセットアップ
description: ドメインサーバーのセットアップ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '93'
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
