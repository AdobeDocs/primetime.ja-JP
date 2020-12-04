---
seo-title: 概要
title: 概要
uuid: 2bbf0aa1-df35-429d-84df-db357fa53e47
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# 概要{#overview}

ライセンスを取得するには、パッケージ化されたコンテンツに埋め込まれたメタデータからクライアントが要求を作成し、その要求をライセンスサーバーに送信します。 ライセンスサーバは、コンテンツメタデータから抽出された情報を用いてライセンスを生成する。

クライアントとサーバーの両方がプロトコルバージョン5をサポートしている場合、要求URLは「License Server URL in metadata」 + &quot; [!DNL /flashaccess/license/v4]」になります。 プロトコルバージョン3がクライアントまたはサーバーでサポートされる最大数である場合、Primetime DRMクライアントは認証要求を「License Server URL in metadata」 + &quot; [!DNL /flashaccess/license/v3]&quot;に送信します。 それ以外の場合は、認証要求は「License Server URL in metadata」 + &quot; [!DNL /flashaccess/license/v1]&quot;に送信されます。

1つのデバイスに同じコンテンツ（同じライセンスID）に対する複数のライセンスを持つことができますが、特定のライセンスIDとDRMポリシーIDに対するライセンスは1つだけ持つことができます。 重複ライセンスID/ポリシーIDを持つライセンスを受け取った場合、新しいライセンスは、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、古いライセンスを置き換えます。 このロジックは、コンテンツに埋め込まれたライセンスを処理するために使用されます。 したがって、同じDRMポリシーIDを持つ複数のライセンスをコンテンツのチャンクに埋め込むことはお勧めしません。 `DRMManager.storeVoucher()`ActionScript3 API経由でクライアントに渡されるライセンスにも同じロジックが適用されます。クライアントが発行日の新しいライセンスを既に所有している場合、提供されたライセンスは無視することができます。

## ライセンス要求処理クラス{#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`  — ライセンスリクエストハンドラークラスです。ライセンス要求を読み取り、解析します。 `getRequests()`メソッドは、`LicenseRequestMessage`オブジェクトのリストを返します。
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`  — これはリクエストメッセージクラスです。呼び出し元は、`getRequests()`から返された`LicenseRequestMessage`リストを繰り返し処理し、各要求に対してライセンスを生成するか、エラーコードを設定する必要があります。 コンテンツID、ライセンスID、DRMポリシーなど、コンテンツメタデータから抽出した情報を取得するには、`LicenseRequestMessage.getContentInfo()`を呼び出します。

ライセンスとエラーは、`LicenseHandler.close()`メソッドが呼び出されると同時に送信されます。

詳しくは、[DRM Server APIリファレンスドキュメント](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html)を参照してください。
