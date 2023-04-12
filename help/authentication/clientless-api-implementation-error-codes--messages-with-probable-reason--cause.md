---
title: クライアントレス API 実装 — エラーコード/推定理由/原因を含むメッセージ
description: クライアントレス API 実装 — エラーコード/推定理由/原因を含むメッセージ
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# クライアントレス API 実装 — エラーコード/推定理由/原因を含むメッセージ {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

</br>


## エラー：許可されていません

### 原因：

1. 認証ヘッダーがPOSTにありません
1. 認証ヘッダーの問題 — リクエスト時間がミリ秒単位かどうかを確認します。

## エラー：認証中の SC 400

### 原因：

1. 特定のリクエスト元および環境用に作成された登録コードがサーバーで見つかりませんでした。
1. クロスドメインスクリプティングの問題が発生する可能性があります
1. /etc/hosts ファイルに適切なスプーフィングを追加する必要があります

## エラー：400 無効なリクエスト

### 原因：

1. POST/GETの URL の形式が正しくありません
1. SAMLAssertionParserException — 暗号化された SAML アサーションをAdobe側で復号化できませんでした

## エラー： 403 Forbidden

### 原因：

1. リクエストが多すぎます — API 管理の機能で、DoS 攻撃を防ぎます。
2. 前の環境を使用する場合は、スプーフィングを追加します。それ以外の場合は、スプーフィングが/etc/hosts ファイルから削除されていることを確認します。

## エラー：MVPD ページにログインできません

### 原因：

1. ユーザー名とパスワードが一致しません 
2. ログインが無効になっている可能性があります
3. ログインが実稼動用かステージング用かを確認します


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->