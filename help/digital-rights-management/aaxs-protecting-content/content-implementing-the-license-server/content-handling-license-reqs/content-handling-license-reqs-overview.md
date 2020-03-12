---
seo-title: 概要
title: 概要
uuid: d3bfa65b-2360-4843-b59e-71451fa62a2c
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 概要{#overview}

ライセンスを要求するために、クライアントはパッケージ化時にコンテンツに埋め込まれたメタデータを送信します。 ライセンスサーバは、コンテンツメタデータの情報を使用してライセンスを生成する。

はライセ `LicenseHandler` ンスリクエストを読み取り、リクエストを解析します。 `LicenseHandler`は、バッ `BatchHandlerBase` チライセンスのリクエストに対応するように拡張されていますが、この機能は現在Adobe Accessクライアントではサポートされていません。 このメソ `getRequests()` ッドは、オブジェクトのListを返 `LicenseRequestMessage` します。 呼び出し元は、を繰り返し処理し、 `LicenseRequestMessages`リクエストごとに、ライセンスを生成するか、エラーコードを設定する必要があります(詳しくは、 `LicenseRequestMessage` APIリファレンスのドキュメントを参照してください)。 サーバーは、ライセンス要求ごとにライセンスを発行するかどうかを決定します。 コンテ `LicenseRequestMessage.getContentInfo()` ンツID、ライセンスID、ポリシーなど、コンテンツメタデータから抽出された情報を取得するための呼び出し。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* クライアントとサーバの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバURL:+ &quot;/flashaccess/license/v4&quot; プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大数の場合、Adobe Accessクライアントは認証要求を「メタデータのライセンスサーバーURL」 + 「/flashaccess/license/v3」に送信します。 それ以外の場合、認証要求は「メタデータのライセンスサーバーURL」 + 「/flashaccess/license/v1」に送信されます。

要求の解析中にエラーが発生した場合、がスロー `HandlerParsingException` されます。 この例外には、クライアントに返すエラー情報が含まれています。 エラー情報を取得するには、を呼び出しま `HandlerParsingException.getErrorData()`す。 ポリシー要件が満たされていないためにライセンスの生成中にエラーが発生した場合、がスロ `PolicyEvaluationException` ーされます。 この例外は、クライアント `ErrorData` に返す必要も含まれます。 ライセンス生成中にポリシーがどのよ `LicenseRequestMessage.generateLicense()` うに評価されるかについて詳しくは、APIのドキュメントを参照してください。

ライセンスとエラーは、が呼び出されたときに一度に `LicenseHandler.close()` 送信されます。

1つのデバイスに同じコンテンツ（同じライセンスID）の複数のライセンスを持つこともできますが、特定のライセンスIDとポリシーIDのライセンスは1つだけ持つことができます。 LicenseID/PolicyIDが重複するライセンスを受け取った場合、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、新しいライセンスが古いライセンスに置き換えられます。 このロジックは、コンテンツに埋め込まれたライセンスを処理するために使用されるので、同じポリシーIDを持つ複数のライセンスをコンテンツのチャンクに埋め込むことはお勧めしません。 同じロジックが、ActionScript3 APIを通じてクライアントに渡されるライセ `DRMManager.storeVoucher()` ンスにも適用されます。クライアントが発行日が新しいライセンスを既に持っている場合、提供されたライセンスは無視される可能性があります。
