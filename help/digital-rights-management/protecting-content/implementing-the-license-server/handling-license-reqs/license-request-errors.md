---
seo-title: ライセンス要求エラー処理
title: ライセンス要求エラー処理
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# {#license-request-error-handling}の処理中にライセンス要求エラーが発生しました

要求の解析中にエラーが発生した場合は、`HandlerParsingException`が発生します。 この例外には、クライアントに返されるエラー情報が含まれます。 エラー情報を取得する必要がある場合は、`HandlerParsingException.getErrorData()`を呼び出す必要があります。 DRMポリシーの要件が満たされていないためにライセンスの生成中にエラーが発生した場合は、`PolicyEvaluationException`が発生します。 この例外には、クライアントに返す`ErrorData`も含まれます。

ライセンス生成中のDRMポリシーの評価方法について詳しくは、`LicenseRequestMessage.generateLicense()`のAPIドキュメントを参照してください。
