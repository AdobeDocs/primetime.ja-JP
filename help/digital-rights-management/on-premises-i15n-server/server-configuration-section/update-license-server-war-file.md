---
title: License Server WARファイルの更新
description: License Server WARファイルの更新
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# License Server WARファイルの更新{#update-the-license-server-war-file}

オンプレミスの個別化サーバーを介して個別化したクライアントをサポートするには、新しく取得した個別化CA秘密鍵証明書を含めるように、License Serverの証明書信頼ルートを更新する必要があります。 Pythonスクリプト([!DNL addIndivCert.py])は、[!DNL update_license_server]フォルダーに含まれています。

次の手順を実行してLicense Serverを更新します。

1. 更新するWARファイルのコピーを作成します(例：[!DNL flashaccess.war]、[!DNL faxsks.war])。
1. WARファイルのロックが解除され、権限が設定されていて、変更できることを確認します。
1. [!DNL addIndivCert.py] Pythonスクリプトを実行して、License Server WARファイルを更新します。

   スクリプトの入力は次のとおりです。

   * `cert`:個別化CA証明書を含むPKCS12ファイル
   * `war`:更新するWARファイル

   出力ファイルは、更新されたWARファイルです。

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

WARファイルが適切に変更されます。 必要に応じて、Pythonスクリプトを編集し、必要に応じて変更を加えることができます。 更新を実行した後、WARファイルを通常どおりデプロイできます。
