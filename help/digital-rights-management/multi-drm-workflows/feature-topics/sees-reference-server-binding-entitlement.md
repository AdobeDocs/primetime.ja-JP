---
description: SEESリファレンスサーバーでは、ExpressPlayを使用してデバイスバインディングのエンタイトルメントサービスを有効にする方法を示します。
seo-description: SEESリファレンスサーバーでは、ExpressPlayを使用してデバイスバインディングのエンタイトルメントサービスを有効にする方法を示します。
seo-title: リファレンスサービスのデバイスバインディングエンタイトルメント
title: リファレンスサービスのデバイスバインディングエンタイトルメント
uuid: 22ce2f8e-1758-4528-8caf-60d209839afe
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# リファレンスサービス：デバイスバインディングのエンタイトルメント {#reference-service-device-binding-entitlement}

SEESリファレンスサーバーでは、ExpressPlayを使用してデバイスバインディングのエンタイトルメントサービスを有効にする方法を示します。

>[!NOTE]
>
>デバイスに対応したエンタイトルメントサービスは、時間制限にすることも、レンタル期間を設定することもできます。

情報をブートスト `device_id` ラップするには、ダミーのM3U8コンテンツを再生します。 その後、ExpressPlayトークンにcookieを埋め込み、SPC（この内容）を生成し、ExpressPlay `device_id`サーバーにを送 `getToken` 信できます。

![](assets/fees-device-binding.png)

シーケンスは、ダミーのM3U8の再生から始まります。 CookieがSEESサーバーに送信され、ExpressPlayトークンのURLが取得されます。 cookieにバインドされたExpressPlayトークンのURLを受け取ったら、次の手順はSPCを生成し、ExpressPlayサーバーに送信することです。 ExpressPlayサーバーは、SPCから `device_id` cookieを抽出し、ExpressPlayトークンのURLからcookieを抽出し、そのcookieとトランザクショ `device_id` ンログに格納します。

クライアントは、同じcookieを送信するSEESに対して実際のライセンスリクエストを行います。 SEESは、ExpressPlayサーバーからCookieを取得するた `device_id` めにCookieを使用します。

SEEは、デバイスにバインドされ、時間にバインドされたExpressPlayトークンを要求し、そのトークンをクライアントに返します。

クライアントは、ExpressPlayトークンを使用してライセンスリクエストを行います。

ExpressPlayサーバーは、SPC内の `device_id` とExpressPlayトークン内のと `device_id` を比較します。 ExpressPlayサーバーは、2つの値が一致する場合にのみライセンス `device_id` を発行します。
