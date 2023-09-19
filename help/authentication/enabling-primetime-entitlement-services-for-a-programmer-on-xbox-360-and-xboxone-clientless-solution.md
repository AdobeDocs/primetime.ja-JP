---
title: Xbox 360 および XboxOne クライアントレスで、プログラマー向けの Primetime エンタイトルメントサービスを有効化
description: Xbox 360 および XboxOne クライアントレスで、プログラマー向けの Primetime エンタイトルメントサービスを有効化
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Xbox 360 および XboxOne クライアントレスで、プログラマー向けの Primetime エンタイトルメントサービスを有効化 {#enabling-primetime-entitlement-services-for-a-programer-on-xbox-360-and-xboxone-clientless}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。




1. プログラマーは、Xbox 360/One for Primetime 認証クライアントレスソリューションを有効にする Zendesk チケットを作成します。次の情報を提供します。

   1. プラットフォーム： Xbox 360、Xbox One など

   1. 要求者 ID:netgeo、CNN など。

1. Adobeは X509 証明書を作成し、最後に秘密鍵とパスワードを設定します。

1. Adobeは（X509 証明書の）公開証明書をチケット内または電子メールでプログラマーに提供します。

1. その後、プログラマーは、Microsoftに登録されたアプリ用の公開証明書を GDNP ポータルにインストールする必要があります。

1. その後、プログラマーは、Xbox Live サービスから XboxOne 用の JWT （Java Web トークン）または STS トークンを要求します。これは、手順 3 で提供された X509 公開証明書を使用して暗号化されます。

1. これは、Xbox デバイス用の一意の deviceId を含むトークンです。 以下のように「x」パラメーターを使用して、Authorization ヘッダーにトークン（JWT または STS）を含めます。

   1. Xbox 360 の場合、XSTS トークンは Base64 エンコードしてから Primetime Pay-TV 認証に送信する必要があります。
   1. Xbox One の場合、JWT は既に正しくエンコードされているので、追加のエンコードは行われません。

1. Xbox デバイスからの API 呼び出しには、x パラメーターに上記のトークンを含む認証ヘッダーを含める必要があります。



>[!NOTE]
>
>特に Xbox には、デジタル署名に関する独自の要件がいくつかあります。 XBox コンソールのデバイス ID は、XSTS トークンに含まれています。  Xbox 360 の場合、これは暗号化された SAML アサーションです。Xbox One の場合は、暗号化された JWT です。 XBox コンソールアプリは、XSTS トークン全体を Primetime ペイテレビ認証に送信します。 Primetime Pay-TV 認証は、公開鍵を使用してトークンを復号化し、トークンを解析して、そこから deviceId を抽出します。

>[!NOTE]
>
>XSTS トークンの長さが大きいので、XBox コンソールには技術的な制限があります。トークンを HTTPGETパラメーターとして Primetime pay-TV 認証 API に送信することはできません。 これに対応するため、Primetime pay-TV 認証では、API を呼び出す際に HTTP ヘッダー「Authorization」の一部として XSTS トークンを送信できます。 XSTS トークンは、Primetime pay-TV 認証からプログラマーに対して発行された X.509 証明書の公開鍵を使用して暗号化する必要があります。 Primetime Pay-TV 認証は、関連する秘密鍵を保存し、それを使用して XSTS トークンを復号化し、そこから deviceId を抽出します。
