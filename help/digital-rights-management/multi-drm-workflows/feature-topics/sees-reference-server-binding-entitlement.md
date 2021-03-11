---
description: SEESリファレンスサーバーでは、ExpressPlayを使用してデバイスバインディングエンタイトルメントサービスを有効にする方法を示しています。
title: リファレンスサービスのデバイスバインディングエンタイトルメント
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# リファレンスサービス：デバイスバインディングエンタイトルメント{#reference-service-device-binding-entitlement}

SEESリファレンスサーバーでは、ExpressPlayを使用してデバイスバインディングエンタイトルメントサービスを有効にする方法を示しています。

>[!NOTE]
>
>デバイスバウンドのエンタイトルメントサービスは、時間制限にすることも、レンタル期間を設定することもできます。

`device_id`情報をブートストラップするには、ダミーのM3U8コンテンツを再生します。 次に、ExpressPlayトークンにCookieを埋め込み、SPC（`device_id`を含む）を生成し、`getToken`をExpressPlayサーバーに送信します。

![](assets/fees-device-binding.png)

ダミーM3U8を再生することによるシーケンス開始。 CookieがSEESサーバーに送信され、ExpressPlayトークンURLが取得されます。 CookieにバウンドされたExpressPlayトークンURLを受け取ったら、次の手順はSPCを生成し、ExpressPlayサーバーに送信することです。 ExpressPlayサーバーは、SPCから`device_id`を抽出し、ExpressPlayトークンURLからcookieを抽出して、Cookieと`device_id`をトランザクションログに配置します。

クライアントは、同じcookieを送信するSEESに対して実際のライセンスリクエストを行います。 SEESはcookieを使用してExpressPlayサーバーから`device_id`を取得します。

SEEは、デバイスにバインドされたExpressPlayトークンとタイムバウンドを要求し、そのトークンをクライアントに返します。

クライアントは、ExpressPlayトークンを使用してライセンスリクエストを行います。

ExpressPlayサーバーは、SPC内の`device_id`とExpressPlayトークン内の`device_id`を比較します。 ExpressPlayサーバーは、2つの`device_id`値が一致する場合にのみライセンスを発行します。
