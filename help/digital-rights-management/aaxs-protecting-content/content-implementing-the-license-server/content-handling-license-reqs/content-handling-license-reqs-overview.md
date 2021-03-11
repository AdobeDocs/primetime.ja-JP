---
title: 概要
description: 概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# 概要{#overview}

ライセンスを要求するために、クライアントはパッケージ化の際にコンテンツに埋め込まれたメタデータを送信します。 ライセンスサーバは、コンテンツメタデータの情報を使用してライセンスを生成する。

`LicenseHandler`はライセンス要求を読み取り、要求を解析します。 `LicenseHandler`は、バッチライセンス要求 `BatchHandlerBase` に対応するように拡張されていますが、この機能は現在、Adobeアクセスクライアントではサポートされていません。`getRequests()`メソッドは、`LicenseRequestMessage`オブジェクトのリストを返します。 呼び出し元は`LicenseRequestMessages`を繰り返し処理し、要求ごとにライセンスを生成するか、エラーコードを設定する必要があります（詳しくは、`LicenseRequestMessage` APIリファレンスドキュメントを参照してください）。 サーバーは、ライセンス要求ごとにライセンスを発行するかどうかを決定します。 コンテンツID、ライセンスID、ポリシーなどのコンテンツメタデータから抽出した情報を取得するには、`LicenseRequestMessage.getContentInfo()`を呼び出します。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`です
* クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバーURL:+ 「/flashaccess/license/v4」)。 プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大数の場合、Adobeアクセスクライアントは認証要求を「License Server URL in metadata」 + &quot;/flashaccess/license/v3&quot;に送信します。 それ以外の場合は、認証要求は「メタデータのライセンスサーバーのURL」 + 「/flashaccess/license/v1」に送信されます。

要求の解析中にエラーが発生した場合は、`HandlerParsingException`がスローされます。 この例外には、クライアントに返すエラー情報が含まれます。 エラー情報を取得するには、`HandlerParsingException.getErrorData()`を呼び出します。 ポリシー要件が満たされていないためにライセンスの生成中にエラーが発生した場合は、`PolicyEvaluationException`がスローされます。 この例外には、クライアントに返す`ErrorData`も含まれます。 ライセンス生成中のポリシーの評価方法について詳しくは、`LicenseRequestMessage.generateLicense()`のAPIドキュメントを参照してください。

ライセンスとエラーは、`LicenseHandler.close()`が呼び出されると同時に送信されます。

1つのデバイスに同じコンテンツの複数のライセンス（同じライセンスID）を持つこともできますが、特定のライセンスIDとポリシーIDに対するライセンスは1つだけ持つことができます。 重複ライセンスID/ポリシーIDのライセンスを受け取った場合、新しいライセンスは、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、古いライセンスに置き換わります。 このロジックはコンテンツに埋め込まれたライセンスの処理に使用されるので、複数のライセンスを同じポリシーIDでコンテンツのチャンクに埋め込むことはお勧めしません。 `DRMManager.storeVoucher()`ActionScript3 API経由でクライアントに渡されるライセンスにも同じロジックが適用されます。クライアントが発行日の新しいライセンスを既に所有している場合、提供されたライセンスは無視することができます。
