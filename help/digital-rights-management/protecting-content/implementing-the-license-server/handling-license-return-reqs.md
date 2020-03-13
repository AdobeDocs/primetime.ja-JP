---
seo-title: ライセンスの返却要求の処理
title: ライセンスの返却要求の処理
uuid: 994df5af-476a-4ee8-b371-8900241be83d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスの返却要求の処理{#handle-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、 `DRMManager.returnVoucher()` Actionscript APIを呼び出してプロセスを開始します。 このAPIは、モードまたはモ `immediateCommit` ードで動作し `confirmFirst` ます。 をに設 `immediateCommit` 定すると、 `true`クライアントは、ライセンスを返却する要求を受け取ったことをライセンスサーバから確認する前に、直ちにローカルライセンスを削除します。 Adobe Primetime DRMライセンスサーバーは要求を処理し、応答をクライアントに送信する必要があります。 ライセンスサーバが、特定のユーザに対するライセンス数を減らすなどの要求を処理するか否かは、ライセンスサーバによって決定される。

* リクエストハンドラークラスは、 `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`
* リクエストメッセージクラスは `com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`

必要な最 `Adobe Primetime DRM` 低限のSDKバージョンはバージョン5です。リクエストURLは「 [!DNL /flashaccess/lreturn/v5]」です。 ドメインの登録解除と同様に、サーバーはを使用して、クライア `getRequestPhase()` ントがライセンス返却をプレビューできるかどうかを判断します。
