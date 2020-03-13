---
seo-title: ライセンス要求エラー処理
title: ライセンス要求エラー処理
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンス要求エラー処理 {#license-request-error-handling}

要求の解析中にエラーが発生した場合は、が発生 `HandlerParsingException` します。 この例外には、クライアントに返されるエラー情報が含まれます。 エラー情報を取得する必要がある場合は、を呼び出す必要がありま `HandlerParsingException.getErrorData()`す。 DRMポリシーの要件が満たされていないためにライセンスの生成中にエラーが発生した場合は、エラーが発生 `PolicyEvaluationException` します。 この例外は、クライアント `ErrorData` に返す必要も含まれます。

ライセンス生成中にDRMポリシーがどのよ `LicenseRequestMessage.generateLicense()` うに評価されるかについて詳しくは、APIのドキュメントを参照してください。
