---
seo-title: ドメインサーバーのセットアップ
title: ドメインサーバーのセットアップ
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---


# ドメインサーバーのセットアップ{#set-up-a-domain-server}

既存のLicense Serverのインストール環境でドメインサーバーを構成するには、次のタスクを実行します。

1. [!DNL tomcat/lib]の下の[!DNL flashaccess-refimpl.properties]ファイルを開きます。

1. `Domain CA certificate`オプションの下で、ドメインCA証明書の詳細を入力します。 この証明書は、ドメイントークンの受け入れに使用されます。
1. `Domain CA credential`オプションの下で、`Domain CA credential certificate (PFX)`の詳細を入力します。 この証明書は、ドメインの証明書とトークンの署名に使用されます。

1. `DomainServerlURL`の値を指定します。 この値がNULLの場合、ドメイン認証が成功する可能性があります。 ただし、ドメインに参加する際に、参加ドメインのエラーが発生します。

