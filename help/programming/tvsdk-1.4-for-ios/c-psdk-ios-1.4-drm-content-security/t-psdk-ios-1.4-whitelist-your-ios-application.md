---
description: アドビのMachotoolsツールを使用して、iOSアプリをホワイトリストに登録できます。
seo-description: アドビのMachotoolsツールを使用して、iOSアプリをホワイトリストに登録できます。
seo-title: iOSアプリケーションをホワイトリストに登録
title: iOSアプリケーションをホワイトリストに登録
uuid: 52ce1dd7-5f10-418e-9916-cec60eae874e
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# iOSアプリケーションをホワイトリストに登録{#whitelist-your-ios-application}

アドビのMachotoolsツールを使用して、iOSアプリをホワイトリストに登録できます。

一般に、TVSDKアプリケーションを完成させる際に、Adobe Primetime DRMコマンドラインツールを使用してアプリをホワイトリストに登録できます。

>[!TIP]
>
>また、これらのツールを使用して、DRMポリシーを作成し、コンテンツを暗号化することもできます。

アプリのホワイトリストに登録すると、保護されたコンテンツはビデオプレーヤーでのみ再生できます。 ただし、iOSアプリケーションのホワイトリストに登録するには、Appleのアプリケーション送信ポリシーで機能する特別な手順を実行する必要があります。

iOSアプリを送信する前に、署名してAppleに公開する必要があります。

>[!NOTE]
>
>Appleは開発者の署名を削除し、独自の証明書を使用してアプリに再署名します。

再署名のため、Apple App Storeに送信する前に生成したホワイトリスト情報は使用できません。

この送信ポリシーを使用するには、アドビが作成したツールをiOSアプリケーションに指示してダイジェスト値を作成し、この値に署名し、この値をiOSアプリケーションに挿入します。 `machotools` iOSアプリに指紋を付けた後、アプリをApple App Storeに送信できます。 ユーザーがApp Storeからアプリを実行すると、Primetime DRMはアプリケーションの指紋を実行時に計算し、以前にアプリケーションに挿入されたダイジェスト値で確認します。 指紋が一致した場合、アプリはホワイトリストに登録されていると確認され、保護されたコンテンツの再生が許可されます。

Adobeツー `machotools` ルは、[!DNL [...]/tools/DRM]フォルダー。

使用するに `machotools`は：

1. キーペアを生成します。

   OpenSSLなどのユーティリティを使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. プロンプトが表示されたら、秘密鍵を保護するためのパスワードを入力します。

   パスワードは12文字以上で、ASCII文字は大文字と小文字を組み合わせた文字と数字を含める必要があります。
1. OpenSSLを使用して強力なパスワードを生成するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl rand -base64 8
   ```

1. 証明書署名要求(CSR)の生成を参照してください。

   OpenSSLを使用してCSRを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. 証明書に自己署名し、任意の期間を入力します。

   次の例では、20年間の有効期限を設定しています。

   ```
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. 自己署名証明書をPKCS#12ファイルに変換します。

   ```
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   自己署名証明書を使用してiOSアプリに署名できます。

1. PFXファイルの場所とパスワードを更新します。
1. Xcodeでアプリケーションを構築する前に、/に移動し **[!UICONTROL Build Phases]** 、次のコ **[!UICONTROL Run Script]** マンドを実行スクリプトに追加してください。

   ```
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. を実行し [!DNL machotools] て、アプリの発行者IDハッシュ値を生成します。

   ```
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. 新しいDRMポリシーを作成するか、既存のポリシーを更新して、返された発行者IDハッシュ値を含めます。
1. を使用し [!DNL AdobePolicyManager.jar]て、返されたPublisher IDハッシュ値、オプションのApp ID、含まれるファイルに最小および最大バージョンの属性を含める新しいDRMポリシーを作成（既存のポリシーを更新） [!DNL flashaccess-tools.properties] します。

   ```
   java -jar libs/AdobePolicyManager.jar new app_whitelist.pol
   ```

1. 新しいDRMポリシーを使用してコンテンツをパッケージ化し、iOSアプリでホワイトリストに登録されたコンテンツの再生を確認します。

