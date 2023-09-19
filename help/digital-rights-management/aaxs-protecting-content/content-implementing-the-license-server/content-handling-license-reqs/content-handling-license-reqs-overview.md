---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# 概要{#overview}

ライセンスを要求する場合、クライアントはパッケージ化時にコンテンツに埋め込まれたメタデータを送信します。 ライセンスサーバは、コンテンツメタデータの情報を使用してライセンスを生成する。

The `LicenseHandler` ライセンスリクエストを読み取り、リクエストを解析します。 `LicenseHandler`extends `BatchHandlerBase` バッチライセンス要求に対応するために、この機能は、現在、Adobeアクセスクライアントではサポートされていません。 The `getRequests()` メソッドは、次のリストを返します： `LicenseRequestMessage` オブジェクト。 呼び出し元は、 `LicenseRequestMessages`を呼び出し、リクエストごとに、ライセンスを生成するか、エラーコードを設定します ( `LicenseRequestMessage` API リファレンスドキュメントを参照してください )。 サーバは、ライセンス要求ごとに、ライセンスを発行するかどうかを決定します。 通話 `LicenseRequestMessage.getContentInfo()` コンテンツメタデータから抽出された情報（コンテンツ ID、ライセンス ID、ポリシーを含む）を取得する。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`
* クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「メタデータのライセンスサーバー URL: + &quot;/flashaccess/license/v4&quot;」になります。 Adobeバージョン 3 がクライアントまたはサーバーでサポートされる最大値の場合、プロトコルアクセスクライアントは認証要求を「メタデータのライセンスサーバー URL」+「/flashaccess/license/v3」に送信します。 それ以外の場合は、認証要求が「メタデータのライセンスサーバー URL」 + 「/flashaccess/license/v1」に送信されます。

リクエストの解析中にエラーが発生した場合、 `HandlerParsingException` がスローされます。 この例外には、クライアントに返されるエラー情報が含まれます。 エラー情報を取得するには、 `HandlerParsingException.getErrorData()`. ポリシー要件が満たされていないため、ライセンスの生成中にエラーが発生した場合、 `PolicyEvaluationException` がスローされます。 この例外には、 `ErrorData` をクライアントに返します。 詳しくは、 API ドキュメントを参照してください。 `LicenseRequestMessage.generateLicense()` を参照してください。

ライセンスとエラーは、 `LicenseHandler.close()` が呼び出されます。

1 つのデバイスに同じコンテンツの複数のライセンス（同じライセンス ID）がある場合でも、特定のライセンス ID とポリシー ID に対して 1 つのライセンスしか持つことができません。 LicenseID/PolicyID が重複するライセンスを受け取った場合、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、新しいライセンスは古いライセンスに置き換えられます。 このロジックは、コンテンツに埋め込まれたライセンスを処理するために使用されるので、同じポリシー ID を持つ複数のライセンスをコンテンツのチャンクに埋め込むことはお勧めしません。 同じロジックが、 `DRMManager.storeVoucher()` ActionScript3 API。クライアントが発行日の新しいライセンスを既に保有している場合、提供されたライセンスは無視される場合があります。
