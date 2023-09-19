---
title: BEES エラーコード
description: BEES エラーコード
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# BEES エラーコード {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

BEES チェック中にエラーが発生した場合、 `DRMErrorEvent` がクライアントに返されます。 このイベントのプロパティを解析して、失敗の特性の詳細を見つけることができます。 考えられるエラーコードのサブセットを以下に示します。

| エラー | 説明 |
|---|---|
| `3304:305` | 認証/承認リクエストを処理しようとした Primetime Cloud DRM からの汎用認証エラー。 通常、BEES の問題とは関係がありません。 このエラーが常に発生する場合は、診断情報と共に Primetime Cloud DRM チームにトラブルチケットを送信する必要があります。 |
| `3329:0` | アプリケーション固有のエラー（BEES Authorizer から）。 サブエラーコードが返されなかった場合は、エラーテキストに問題の詳細が表示されます。 例えば、応答の解析中に問題が発生したか、BEES サーバーに到達できませんでした。 |
| `3329:<HTTP error code>` | 200 以外の HTTP 応答が BEES サーバによって発行されました。 HTTP エラーコードがサブエラーコードフィールドでクライアントに返されます。 これは、構成の問題、または BEES サーバの停止を示す可能性があります。 |
| `3329:<x>` | BEES サーバーがライセンス要求を許可しませんでした。 サブエラーコードとエラーテキストは、BEES サーバーによって JSON 応答の `error` および `errorText` プロパティ。 この種の応答は、誤りと見なすべきではなく、BEES サーバからの定期的な拒否応答と見なすべきです。 |
