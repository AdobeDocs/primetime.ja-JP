---
description: iOSアプリは、アドビのMachotoolsツールを使用して許可リストできます。
seo-description: iOSアプリは、アドビのMachotoolsツールを使用して許可リストできます。
seo-title: iOSアプリケーションの許可リスト
title: iOSアプリケーションの許可リスト
uuid: bc558f5f-d4e6-4c1c-81eb-f8bd61c63016
translation-type: tm+mt
source-git-commit: 9c6a6f0b5ecff78796e37daf9d7bdb9fa686ee0c
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# iOSアプリケーションの許可リスト {#allowlist-your-ios-application}

iOSアプリは、アドビのMachotoolsツールを使用して許可リストできます。

一般に、TVSDKアプリケーションを完成させる際は、Adobe Primetime DRMコマンドラインツールを使用してアプリを許可リストできます。

>[!TIP]
>
>これらのツールを使用して、DRMポリシーを作成し、コンテンツを暗号化することもできます。

アプリのリストを許可すると、保護されたコンテンツは確実にビデオプレーヤーでのみ再生できます。 ただし、iOSアプリケーションのリストを許可するには、Appleのアプリケーション送信ポリシーで機能する特別な手順を実行する必要があります。

iOSアプリを送信する前に、署名してAppleに公開する必要があります。

>[!NOTE]
>
>Appleは、開発者の署名を削除し、独自の証明書を使用してアプリに再署名します。

再署名のため、Apple App Storeに送信する前に生成した許可リスト情報は使用できません。

この送信ポリシーを使用するために、アドビは、iOSアプリケーションにダイジェスト値を作成し、この値に署名し、iOSアプリケーションにこの値を挿入するための指示を行う `machotools` ツールを作成しました。 iOSアプリに指紋を付けた後、アプリをApple App Storeに送信できます。 ユーザーがApp Storeからアプリを実行すると、Primetime DRMはアプリケーション指紋の実行時計算を実行し、以前にアプリケーションに挿入された要約値で確認します。 指紋が一致した場合、アプリが許可されていることが確認され、保護されたコンテンツの再生が許可されます。

Adobe `machotools` ツールは、iOS TVSDK SDKの[!DNL [...]/tools/DRM]フォルダーに置き換えます。

使用する手順 `machotools`:

1. キーペアを生成します。

   OpenSSLなどのユーティリティを使用するには、コマンドウィンドウを開き、次のように入力します。

   ```
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. 秘密鍵を保護するためのパスワードを要求されたら、入力します。

   パスワードは12文字以上にする必要があり、文字には、ASCII文字と数字の大文字と小文字を組み合わせたものを含める必要があります。
1. OpenSSLを使用して堅牢なパスワードを生成するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl rand -base64 8
   ```

1. 証明書署名要求(CSR)を生成します。

   OpenSSLを使用してCSRを生成するには、コマンドウィンドウを開いて次のように入力します。

   ```
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. 証明書に自己署名し、任意の期間を入力します。

   次の例では、20年間の有効期限が設定されています。

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

1. PFXファイルとパスワードの場所を更新します。
1. Xcodeでアプリケーションを構築する前に、 **[!UICONTROL Build Phases]** /に移動し、次のコマンド **[!UICONTROL Run Script]** を実行スクリプトに追加します。

   ```
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. を実行 [!DNL machotools] して、アプリのPublisher IDハッシュ値を生成します。

   ```
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. 新しいDRMポリシーを作成するか、既存のポリシーを更新して、返された発行者IDハッシュ値を含めます。
1. を使用して、新しいDRMポリシーを作成し（既存のポリシーを更新）、返されたPublisher IDハッシュ値、オプションのアプリID、最小および最大バージョンの属性を含めた [!DNL AdobePolicyManager.jar][!DNL flashaccess-tools.properties] ファイルを作成します。

   ```
   java -jar libs/AdobePolicyManager.jar new app_whitelist.pol
   ```

1. 新しいDRMポリシーを使用してコンテンツをパッケージ化し、iOSアプリで許可一覧のコンテンツの再生を確認します。
