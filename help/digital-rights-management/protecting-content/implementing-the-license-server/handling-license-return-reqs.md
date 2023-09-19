---
title: ライセンス返品要求の処理
description: ライセンス返品要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# ライセンス返品要求の処理{#handle-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、 `DRMManager.returnVoucher()` プロセスを開始する ActionScript API です。 この API は `immediateCommit` モードまたは `confirmFirst` モード。 次の場合 `immediateCommit` が `true`を指定した場合、クライアントは直ちにローカルライセンスを削除します。ライセンスサーバーから、ライセンスの返却要求を受け取ったことの確認を待たずに済みます。 Adobe Primetime DRM ライセンスサーバーが要求を処理し、応答をクライアントに送信する必要があります。 ライセンスサーバが、特定のユーザに対するライセンス数を減らす等の要求を処理するか否かは、ライセンスサーバによって決定される。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* リクエストメッセージクラスは、 `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

最小 `Adobe Primetime DRM` 必要な SDK のバージョンはバージョン 5 です。リクエスト URL は「 [!DNL /flashaccess/lreturn/v5]&quot;. ドメインの登録解除と同様に、サーバーは `getRequestPhase()` をクリックして、クライアントがライセンスリターンをプレビューできるかどうかを判断します。
