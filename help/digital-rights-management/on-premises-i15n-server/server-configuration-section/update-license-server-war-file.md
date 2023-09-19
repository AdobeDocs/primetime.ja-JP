---
title: License Server WAR ファイルの更新
description: License Server WAR ファイルの更新
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# License Server WAR ファイルの更新{#update-the-license-server-war-file}

On Premises Individualization Server を介して個別化したクライアントをサポートするには、新しく取得した個別化 CA の資格情報を含めるように、ライセンスサーバーの信頼の証明書ルートを更新する必要があります。 Python スクリプト ( [!DNL addIndivCert.py]) が [!DNL update_license_server] フォルダー。

ライセンスサーバを更新するには、次の手順を実行します。

1. 更新する WAR ファイルのコピーを作成します ( 例： [!DNL flashaccess.war], [!DNL faxsks.war]) をクリックします。
1. WAR ファイルのロックが解除され、権限が設定されていることを確認して、変更できるようにします。
1. を実行します。 [!DNL addIndivCert.py] License Server WAR ファイルを更新する Python スクリプト。

   スクリプトの入力は次のとおりです。

   * `cert`：個別化 CA 証明書を含む PKCS12 ファイル
   * `war`：更新する WAR ファイル

   出力ファイルは、更新された WAR ファイルです。

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

WAR ファイルがその場で変更されます。 必要に応じて、Python スクリプトを編集し、必要に応じて変更を加えることができます。 更新を実行した後、WAR ファイルを通常どおりデプロイできます。
