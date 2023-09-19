---
title: ドメインサーバーの設定
description: ドメインサーバーの設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---

# ドメインサーバーの設定{#set-up-a-domain-server}

既存のライセンスサーバーインストールでドメインサーバーを構成するには、次の手順に従います。

1. Adobe Analytics の [!DNL tomcat/lib] ディレクトリに移動し、 [!DNL flashaccess-refimpl.properties] ファイル。
1. の下 `Domain CA certificate` オプションで、ドメイン CA 証明書を入力します。

   その後、この証明書はドメイントークンの受け入れに使用されます。
1. の下 `Domain CA credential` オプションを選択し、 `Domain CA credential certificate (PFX)` 詳細。

   その後、この証明書はドメイン証明書およびトークンへの署名に使用されます。
1. 次の値を指定： `DomainServerlURL`.

   この値が `NULL`の場合、ドメイン認証が成功する可能性があります。 ただし、ドメインに参加する際に、結合ドメインエラーが発生する場合があります。
