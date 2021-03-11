---
title: ライセンス要求エラー処理
description: ライセンス要求エラー処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# {#license-request-error-handling}の処理中にライセンス要求エラーが発生しました

要求の解析中にエラーが発生した場合は、`HandlerParsingException`が発生します。 この例外には、クライアントに返されるエラー情報が含まれます。 エラー情報を取得する必要がある場合は、`HandlerParsingException.getErrorData()`を呼び出す必要があります。 DRMポリシーの要件が満たされていないためにライセンスの生成中にエラーが発生した場合は、`PolicyEvaluationException`が発生します。 この例外には、クライアントに返す`ErrorData`も含まれます。

ライセンス生成中のDRMポリシーの評価方法について詳しくは、`LicenseRequestMessage.generateLicense()`のAPIドキュメントを参照してください。
