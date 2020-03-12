---
seo-title: 概要
title: 概要
uuid: 2bbf0aa1-df35-429d-84df-db357fa53e47
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# 概要 {#overview}

ライセンスを取得するには、クライアントはパッケージ化されたコンテンツに埋め込まれたメタデータからリクエストを作成し、そのリクエストをライセンスサーバに送信します。 ライセンスサーバは、コンテンツメタデータから抽出された情報を用いてライセンスを生成する。

クライアントとサーバの両方がプロトコルバージョン5をサポートしている場合、要求URLは「メタデータのライセンスサーバのURL」 + 「」にな [!DNL /flashaccess/license/v4]ります。 プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大値である場合、Primetime DRMクライアントは認証要求を「メタデータのライセンスサーバーURL」 + 「」に送信し [!DNL /flashaccess/license/v3]ます。 それ以外の場合、認証要求は「メタデータのライセンスサーバURL」 + 「」に送信され [!DNL /flashaccess/license/v1]ます

1つのデバイスに同じコンテンツ（同じライセンスID）の複数のライセンスを持つことができますが、特定のライセンスIDとDRMポリシーIDのライセンスは1つだけ持つことができます。 LicenseID/PolicyIDが重複するライセンスを受け取った場合、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、新しいライセンスが古いライセンスを置き換えます。 このロジックは、コンテンツに埋め込まれたライセンスを処理するために使用されます。 したがって、同じDRMポリシーIDを持つ複数のライセンスをコンテンツのチャンクに埋め込むことはお勧めしません。 同じロジックが、ActionScript3 APIを通じてクライアントに渡されるライセ `DRMManager.storeVoucher()` ンスにも適用されます。クライアントが発行日が新しいライセンスを既に持っている場合、提供されたライセンスは無視される可能性があります。

## ライセンス要求処理クラス {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`  — これは、ライセンスリクエストハンドラークラスです。 ライセンス要求を読み取って解析します。 このメソ `getRequests()` ッドは、オブジェクトのリストを返 `LicenseRequestMessage` します。
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`  — これはリクエストメッセージクラスです。 呼び出し元は、によって返され `LicenseRequestMessage` たリストを繰り返し処理し、 `getRequests()`要求ごとにライセンスを生成するか、エラーコードを設定する必要があります。 コンテ `LicenseRequestMessage.getContentInfo()` ンツID、ライセンスID、DRMポリシーなど、コンテンツメタデータから抽出された情報を取得するための呼び出し。

ライセンスとエラーは、メソッドが呼び出されたとき `LicenseHandler.close()` に一度に送信されます。

詳しくは、 [DRMサーバーAPIリファレンスドキュメントを参照](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) してください。
