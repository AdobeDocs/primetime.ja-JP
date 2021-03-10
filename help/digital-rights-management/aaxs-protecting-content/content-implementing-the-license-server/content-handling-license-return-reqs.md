---
title: ライセンスの返却要求の処理
description: ライセンスの返却要求の処理
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# ライセンスの返却要求の処理{#handling-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、DRMManager.returnVoucher() Actionscript APIを呼び出してプロセスを開始します。 このAPIは、immediateCommitモードまたはconfirmFirstモードで動作します。 immediateCommitをtrueに設定すると、クライアントは、ライセンスの返却要求を受け取ったことをライセンスサーバから確認する前に、直ちにローカルライセンスを削除します。 Adobeアクセスライセンスサーバーは、要求を処理し、クライアントに応答を送信する必要があります。 ライセンスサーバが要求に対して実際に何かを行うかどうか（特定のユーザのライセンス数を減らすなど）は、ライセンスサーバが決定します。

* リクエストハンドラークラスは、com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandlerです。
* リクエストメッセージクラスは、com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessageです。

必要なAdobeアクセスSDKの最小バージョンは、バージョン5です。リクエストURLは「`/flashaccess/lreturn/v5`」になります。 ドメイン登録解除と同様に、サーバーは`getRequestPhase()`を使用して、クライアントがライセンスの返却をプレビューしているかどうかを確認する必要があります。
