---
description: ライセンス認証とポリシーの適用を調整する1つの方法は、エンタイトルメントサーバーにこれらの機能を組み込むことです。 Adobeは、独自のサーバーを構築する際に使用できるSEES参照エンタイトルメントサーバーを提供します。
title: リファレンスサーバーのサンプルExpressPlayエンタイトルメントサーバー(SEE)
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# 参照サーバー：ExpressPlayエンタイトルメントサーバーの例(SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

ライセンス認証とポリシーの適用を調整する1つの方法は、エンタイトルメントサーバーにこれらの機能を組み込むことです。 Adobeは、独自のサーバーを構築する際に使用できるSEES参照エンタイトルメントサーバーを提供します。

リファレンスサーバーSEEには、ExpressPlay Entitlement Serviceの例が示され、次の2つのサービスが表示されます。基本的な時間ベースの権利付与とデバイスバインディングの権利付与。

SEESは、2つのExpressPlay FairPlay Servicesの上に構築されています。

1. Expressplayトークンリクエストサービス
1. Expressplayレコード取得サービス

ExpressPlay TokenリクエストのURL形式は、実稼働用とテスト環境用の2つの形式を取ります。

**実稼働**:<span></span>https://fp-gen.{prod_domain}/hms/fp/token

**テスト**:<span></span>https://fp-gen.test.expressplay.com/hms/fp/token

ExpressPlayレコードを取得するためのURL形式は、実稼働用とテスト環境用の2つのフォームを取ります。

**実稼働**:<span></span>https://api.{prod_domain}/cmiapi/getrecord/

**テスト**:<span></span>https://api.test.expressplay.com/cmiapi/getrecord/
