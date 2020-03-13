---
seo-title: License Server WARファイルの更新
title: License Server WARファイルの更新
uuid: 0cde53d6-185d-4bf2-84fc-0c31d17904a8
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# License Server WARファイルの更新{#update-the-license-server-war-file}

オンプレミス個別化サーバーを介して個別化したクライアントをサポートするには、新しく取得した個別化CA証明書を含めるように、ライセンスサーバーの証明書信頼のルートを更新する必要があります。 Pythonスクリプト( [!DNL addIndivCert.py])がフォルダに含まれ [!DNL update_license_server] ます。

次の手順を実行して、License Serverを更新します。

1. 更新するWARファイルのコピーを作成します(例： [!DNL flashaccess.war]、 [!DNL faxsks.war])。
1. WARファイルのロックが解除され、権限が設定されていることを確認して、ファイルを変更できるようにします。
1. Pythonスクリプトを [!DNL addIndivCert.py] 実行して、License Server WARファイルを更新します。

   スクリプトの入力は次のとおりです。

   * `cert`:個別化CA証明書を含むPKCS12ファイル
   * `war`:更新するWARファイル
   出力ファイルは、更新されたWARファイルです。

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

WARファイルが適切に変更されます。 必要に応じて、Pythonスクリプトを編集し、ニーズに合わせて編集できます。 更新を実行した後、WARファイルを通常どおりにデプロイできます。
