---
description: ライセンスとポリシーの実施を調整する方法の 1 つは、権限付与サーバーにこれらの機能を組み込むことです。 Adobeは、 SEES 参照権限付与サーバーを提供します。このサーバーは、と連携して独自のサーバーを作成できます。
title: 参照サーバー ExpressPlay エンタイトルメントサーバー (SEES) のサンプル
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 参照サーバー： ExpressPlay 使用権限サーバーの例 (SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

ライセンスとポリシーの実施を調整する方法の 1 つは、権限付与サーバーにこれらの機能を組み込むことです。 Adobeは、 SEES 参照権限付与サーバーを提供します。このサーバーは、と連携して独自のサーバーを作成できます。

参照サーバー SEES は、ExpressPlay エンタイトルメントサービスの例を示し、基本的な時間ベースのエンタイトルメントとデバイスバインディングのエンタイトルメントの 2 つのサービスを示します。

SEES は、2 つの ExpressPlay Fairplay サービスの上に構築されています。

1. Expressplay トークンリクエストサービス
1. Expressplay レコード取得サービス

ExpressPlay トークンリクエストの URL 形式は、実稼動用、テスト環境用の 2 つの形式を取ります。

**実稼動**: ht<span></span>tps://fp-gen.{prod_domain}/hms/fp/token

**テスト**: ht<span></span>tps://fp-gen.test.expressplay.com/hms/fp/token

ExpressPlay レコードを取得する際の URL 形式は、実稼動用とテスト環境用の 2 つの形式を取ります。

**実稼動**: ht<span></span>tps://api.{prod_domain}/cmiapi/getrecord/

**テスト**: ht<span></span>tps://api.test.expressplay.com/cmiapi/getrecord/
