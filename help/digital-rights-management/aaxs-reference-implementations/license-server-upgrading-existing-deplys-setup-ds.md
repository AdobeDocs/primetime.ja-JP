---
seo-title: ドメインサーバーの設定
title: ドメインサーバーの設定
uuid: b262ea86-f465-4ed1-b278-122d4dafc881
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ドメインサーバーの設定 {#set-up-a-domain-server}

既存のライセンスサーバーのインストール環境でドメインサーバーを設定するには、次のタスクを実行します。

1. の下のファイル [!DNL flashaccess-refimpl.properties] を開きま [!DNL tomcat/lib]す。

1. このオプション `Domain CA certificate` で、ドメインCA証明書の詳細を入力します。 この証明書は、ドメイントークンの受け入れに使用されます。
1. オプション `Domain CA credential` で、詳細を入力し `Domain CA credential certificate (PFX)` ます。 この証明書は、ドメインの証明書とトークンの署名に使用されます。

1. の値を指定します `DomainServerlURL`。 この値がNULLの場合、ドメイン認証が成功する可能性があります。 ただし、ドメインに参加する際に、参加ドメインエラーが発生します。

