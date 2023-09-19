---
title: Clientless API の実装-考えられる理由/原因を伴うコードとメッセージをエラーします。
description: Clientless API の実装-考えられる理由/原因を伴うコードとメッセージをエラーします。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Clientless API の実装-考えられる理由/原因を伴うコードとメッセージをエラーします。 {#clientless-api-implementation--error-codes-messages-with-probable-reason-cause}

>[!NOTE]
>
>このページの内容は、情報目的でのみ提供されています。 この API を使用するには、Adobe Systems の現在のライセンス版が必要です。 不正な使用は許可されていません。

</br>


## エラー: 承認されていません

### 原因：

1. POST に認証ヘッダーが見つかりません
1. 認証ヘッダーに関する問題-リクエスト時間がミリ秒単位であるかどうかを確認します。

## エラー: 認証中の SC 400

### 原因：

1. サーバーで、特定のリクエスターと環境に対して作成された登録コードが見つかりませんでした。
1. クロスドメインスクリプトの問題が発生している可能性があります。
1. 適切なスプーフィングを/etc/hosts ファイルに追加する必要があります。

## エラー: 400 Bad Request

### 原因：

1. POST/GET の形式が正しくない url
1. SAMLAssertionParserException –暗号化された SAML assertion を Adobe Systems の最後で復号化できない

## エラー: 403 許可されていません

### 原因：

1. ラピッド要求が多すぎます-DoS 攻撃を防ぐための API 管理の機能です。
2. Prequal を使用してスプーフィング環境した場合、または/etc/hosts ファイルからスプーフィングが削除されていることを確認してください。

## エラー: MVPD にログインできませんページ

### 原因：

1. ユーザー名とパスワードが一致しません
2. ログインが無効になっている可能性があります
3. ログインが実稼動用かステージング用かを確認します。


<!--

## Related Information

- [Clientless API Reference](/help/authentication/rest-api-reference.md)

-->
