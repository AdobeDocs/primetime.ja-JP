---
title: BEESエラーコード
description: BEESエラーコード
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# BEESエラーコード{#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

BEESチェック中にエラーが発生した場合、`DRMErrorEvent`がクライアントに返されます。 このイベントのプロパティを解析して、失敗の性質の詳細を調べることができます。 考えられるエラーコードのサブセットを以下に示します。

| エラー | 説明 |
|---|---|
| `3304:305` | Primetime Cloud DRMが認証/認証要求を処理しようとした場合に発生する一般的な認証エラーです。 通常、BEESの問題とは関連しません。 このエラーが常に発生する場合は、診断情報と共にPrimetime Cloud DRMチームにトラブルチケットを送信する必要があります。 |
| `3329:0` | アプリケーション固有のエラー（BEES Authorizerから） サブエラーコードが返されなかった場合は、エラーテキストに問題の詳細が表示されます。 例えば、応答の解析中に問題が発生したか、BEESサーバーが未到達であったかなどです。 |
| `3329:<HTTP error code>` | 200以外のHTTP応答がBEESサーバーによって発行されました。 HTTPエラーコードは、クライアントのサブエラーコードフィールドに返されます。 これは、設定の問題、またはBEESサーバの停止を示す可能性があります。 |
| `3329:<x>` | BEESサーバーはライセンス要求を許可しませんでした。 サブエラーコードとエラーテキストは、BEESサーバーによってJSON応答の`error`プロパティと`errorText`プロパティ内に指定されます。 この種の反応は誤りとは見なされず、むしろBEESサーバからの定期的な拒否応答と見なすべきです。 |