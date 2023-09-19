---
title: ライセンス返品要求の処理
description: ライセンス返品要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---

# ライセンス返品要求の処理{#handling-license-return-requests}

クライアントアプリケーションがライセンスを返す必要がある場合は、 DRMManager.returnVoucher() Actionscript API を呼び出してプロセスを開始します。 この API は、immediateCommit モードまたは confirmFirst モードで動作できます。 immediateCommit が true に設定されている場合、クライアントは直ちにローカルライセンスを削除し、ライセンスサーバからライセンスの返却要求を受け取ったことを確認する必要はありません。 Adobeアクセスライセンスサーバーが要求を処理し、応答をクライアントに送信する必要があります。 ライセンスサーバが要求で実際に何かを行うか（特定のユーザのライセンス数を減らすなど）は、ライセンスサーバが決定する必要があります。

* リクエストハンドラークラスは、 com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnHandler です。
* リクエストメッセージクラスは com.adobe.flashaccess.sdk.protocol.licensereturn.LicenseReturnRequestMessage です。

必要なAdobeアクセス SDK の最小バージョンはバージョン 5 です。リクエスト URL は「 `/flashaccess/lreturn/v5`&quot;. ドメインの登録解除と同様に、サーバーは `getRequestPhase()` をクリックして、クライアントがライセンスリターンをプレビューしているかどうかを確認します。
