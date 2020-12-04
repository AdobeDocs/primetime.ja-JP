---
seo-title: ライセンス返品要求の処理
title: ライセンス返品要求の処理
uuid: 994df5af-476a-4ee8-b371-8900241be83d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# ライセンスの返却要求を処理する{#handle-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、`DRMManager.returnVoucher()` Actionscript APIを呼び出してプロセスを開始します。 このAPIは`immediateCommit`モードまたは`confirmFirst`モードで動作します。 `immediateCommit`を`true`に設定した場合、クライアントは、ライセンスの返却要求を受け取ったというライセンスサーバーからの確認を待たずに、直ちにローカルライセンスを削除します。 Adobe PrimetimeDRMライセンスサーバーは要求を処理し、応答をクライアントに送信する必要があります。 ライセンスサーバは、特定のユーザに対するライセンス数を減らすなど、要求を処理するか否かをライセンスサーバで決定する。

* リクエストハンドラークラスは`com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler`です
* 要求メッセージクラスは`com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage`です

必要な`Adobe Primetime DRM` SDKの最小バージョンはバージョン5；です。リクエストURLは「[!DNL /flashaccess/lreturn/v5]」です。 ドメイン登録解除と同様に、サーバーは`getRequestPhase()`を使用して、クライアントがライセンスの返却をプレビューできるかどうかを判断します。
