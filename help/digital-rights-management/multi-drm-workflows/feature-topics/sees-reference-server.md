---
description: ライセンスとポリシーの実施を調整する1つの方法は、エンタイトルメントサーバーにこれらの機能を組み込むことです。 アドビは、独自のサーバーを構築する際に使用できるSEES参照エンタイトルメントサーバーを提供しています。
seo-description: ライセンスとポリシーの実施を調整する1つの方法は、エンタイトルメントサーバーにこれらの機能を組み込むことです。 アドビは、独自のサーバーを構築する際に使用できるSEES参照エンタイトルメントサーバーを提供しています。
seo-title: リファレンスサーバーサンプルExpressPlayエンタイトルメントサーバー(SEE)
title: リファレンスサーバーサンプルExpressPlayエンタイトルメントサーバー(SEE)
uuid: 99e42f76-7730-42fc-a9a9-f6396ac12c02
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 参照サーバ：ExpressPlayエンタイトルメントサーバーの例(SEE) {#reference-server-sample-expressplay-entitlement-server-sees}

ライセンスとポリシーの実施を調整する1つの方法は、エンタイトルメントサーバーにこれらの機能を組み込むことです。 アドビは、独自のサーバーを構築する際に使用できるSEES参照エンタイトルメントサーバーを提供しています。

リファレンスサーバーSEEは、ExpressPlay Entitlement Serviceの例を示し、次の2つのサービスを示します。基本的な時間ベースの権利付与とデバイスバインディングの権利付与。

SEESは、2つのExpressPlay Fairplayサービスの上に構築されています。

1. Expressplayトークンリクエストサービス
1. Expressplayレコード取得サービス

ExpressPlay TokenリクエストのURL形式は、実稼働用とテスト環境用の2つの形式を取ります。

**実稼働**:https://fp-genを参照し<span></span>てください。{prod_domain}/hms/fp/token

**テスト**:https://fp-gen.test.expressplay.com/hms/fp/token<span></span>

ExpressPlayレコードを取得するためのURL形式は、実稼働用とテスト環境用の2つのフォームを取ります。

**実稼働**:https://apiを参照し<span></span>てください。{prod_domain}/cmiapi/getrecord/

**テスト**:https://api.test.expressplay.com/cmiapi/getrecord/<span></span>
