---
title: ライセンスリクエストのエラー処理
description: ライセンスリクエストのエラー処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# ライセンスリクエストのエラー処理 {#license-request-error-handling}

リクエストの解析中にエラーが発生した場合、 `HandlerParsingException` が発生します。 この例外には、クライアントに返されるエラー情報が含まれます。 エラー情報を取得する必要がある場合は、を呼び出す必要があります。 `HandlerParsingException.getErrorData()`. DRM ポリシーの要件が満たされていないためにライセンスの生成中にエラーが発生した場合、 `PolicyEvaluationException` が発生します。 この例外には、 `ErrorData` をクライアントに返します。

詳しくは、 API ドキュメントを参照してください。 `LicenseRequestMessage.generateLicense()` を参照してください。
