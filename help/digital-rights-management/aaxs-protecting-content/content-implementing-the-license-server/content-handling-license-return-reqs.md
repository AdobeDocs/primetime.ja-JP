---
seo-title: ライセンスの返却要求の処理
title: ライセンスの返却要求の処理
uuid: d184faea-88cb-44f3-a253-e5314d577f17
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスの返却要求の処理{#handling-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、DRMManager.returnVoucher() Actionscript APIを呼び出してプロセスを開始します。 このAPIは、immediateCommitモードまたはconfirmFirstモードで動作します。 immediateCommitがtrueに設定されている場合、クライアントは、ライセンスの返却要求を受け取ったことをライセンスサーバから確認する前に、ローカルライセンスを直ちに削除します。 Adobe Accessライセンスサーバーは、要求を処理し、応答をクライアントに送信する必要があります。 ライセンスサーバが要求を実際に実行する（特定のユーザのライセンス数を減らすなど）かどうかは、ライセンスサーバの判断の対象となります。

* リクエストハンドラークラスは、com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandlerです。
* リクエストメッセージクラスは、com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessageです。

必要なAdobe Access SDKの最小バージョンはバージョン5です。リクエストURLは「 `/flashaccess/lreturn/v5`」です。 ドメインの登録解除と同様に、クライアントがライセンスの返却をプレビ `getRequestPhase()` ューしているかどうかをサーバーが判断する際に使用します。
