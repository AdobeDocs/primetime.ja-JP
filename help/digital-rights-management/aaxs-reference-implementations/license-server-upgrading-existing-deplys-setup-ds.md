---
title: ドメインサーバーの設定
description: ドメインサーバーの設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# ドメインサーバーの設定 {#set-up-a-domain-server}

既存のライセンスサーバーインストール上でドメインサーバーを構成するには、次のタスクを実行します。

1. を開きます。 [!DNL flashaccess-refimpl.properties] ～の下に立ち入る [!DNL tomcat/lib].

1. の下 `Domain CA certificate` オプションで、ドメイン CA 証明書の詳細を入力します。 この証明書は、ドメイントークンの受け入れに使用されます。
1. の下 `Domain CA credential` オプション、 `Domain CA credential certificate (PFX)` 詳細。 この証明書は、ドメイン証明書およびトークンへの署名に使用されます。

1. 次の値を指定： `DomainServerlURL`. この値が NULL の場合、ドメイン認証が成功する可能性があります。 ただし、ドメインに参加する際には、ドメイン参加エラーが発生します。
