---
title: 概要
description: 概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# 概要 {#overview}

ライセンスを取得するために、クライアントはパッケージ化されたコンテンツに埋め込まれたメタデータからリクエストを作成し、そのリクエストをライセンスサーバーに送信します。 ライセンスサーバは、コンテンツメタデータから抽出された情報を用いてライセンスを生成する。

クライアントとサーバーの両方がプロトコルバージョン 5 をサポートしている場合、要求 URL は「メタデータのライセンスサーバー URL」+「」です。 [!DNL /flashaccess/license/v4]&quot;. プロトコルバージョン 3 がクライアントまたはサーバーでサポートされる最大値の場合、Primetime DRM クライアントは認証要求を「メタデータのライセンスサーバー URL」+「」に送信します。 [!DNL /flashaccess/license/v3]&quot;. それ以外の場合は、認証要求は「メタデータのライセンスサーバー URL」+「 」に送信されます。 [!DNL /flashaccess/license/v1]&quot;

1 つのデバイスに同じコンテンツの複数のライセンス（同じライセンス ID）がある場合でも、特定のライセンス ID と DRM ポリシー ID に対して 1 つのライセンスしか持つことはできません。 LicenseID/PolicyID が重複するライセンスを受け取った場合、新しいライセンスの発行日が既存のライセンスの発行日より後の場合にのみ、新しいライセンスは古いライセンスに置き換えられます。 このロジックは、コンテンツに埋め込まれたライセンスを処理するために使用されます。 したがって、同じ DRM ポリシー ID を持つ複数のライセンスをコンテンツのチャンクに埋め込むことはお勧めしません。 同じロジックが、 `DRMManager.storeVoucher()` ActionScript3 API。クライアントが発行日の新しいライセンスを既に保有している場合、提供されたライセンスは無視される場合があります。

## ライセンスリクエスト処理クラス {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler`  — ライセンスリクエストハンドラークラスです。 ライセンス要求を読み取り、解析します。 Its `getRequests()` メソッドは、 `LicenseRequestMessage` オブジェクト。
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage`  — これはリクエストメッセージクラスです。 呼び出し元は、 `LicenseRequestMessage` が返したリスト `getRequests()`を呼び出し、リクエストごとに、ライセンスを生成するか、エラーコードを設定します。 通話 `LicenseRequestMessage.getContentInfo()` コンテンツ ID、ライセンス ID、DRM ポリシーを含むコンテンツメタデータから抽出された情報を取得する。

ライセンスとエラーは、 `LicenseHandler.close()` メソッドが呼び出されます。

詳しくは、 [DRM Server API リファレンスドキュメント](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) 」を参照してください。
