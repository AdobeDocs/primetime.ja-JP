---
description: iOSアプリの許可リストは、Adobeのマコツールを使用して設定できます。
title: iOSアプリケーションの許可リスト
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# iOSアプリケーションの許可リスト {#allowlist-your-ios-application}

iOSアプリの許可リストは、Adobeのマコツールを使用して設定できます。

一般に、 TVSDK アプリケーションを完了する場合は、 Adobe Primetime DRM コマンドラインツールを使用してアプリを許可リスト化できます。

>[!TIP]
>
>また、これらのツールを使用して DRM ポリシーを作成し、コンテンツを暗号化することもできます。

アプリを許可リストに登録すると、保護されたコンテンツをビデオプレーヤーでのみ再生できます。 ただし、iOSアプリケーションを許可リストに登録するには、Appleのアプリケーション送信ポリシーに対応する特別な手順を実行する必要があります。

iOSアプリを送信する前に、署名し、Appleに公開する必要があります。

>[!NOTE]
>
>Appleは、開発者の署名を削除し、アプリケーションに独自の証明書で再署名します。

再署名により、Apple App Storeに送信する前に生成した許可リストへの登録情報は使用できません。

この送信ポリシーを扱うために、Adobeは `machotools` iOSアプリケーションを指紋でダイジェスト値を作成し、この値に署名し、iOSアプリケーションにこの値を挿入するツールです。 iOSアプリをフィンガープリントした後、Apple App Storeにアプリを送信できます。 ユーザーがApp Storeからアプリを実行すると、Primetime DRM はアプリケーションのフィンガープリントを実行し、以前にアプリケーションに挿入されたダイジェスト値で確認します。 指紋が一致した場合、アプリが許可リストに登録されていることが確認され、保護されたコンテンツの再生が許可されます。

Adobe `machotools` ツールは、[!DNL [...]/tools/DRM] フォルダーに保存されます。

次を使用するには： `machotools`:

1. キーペアを生成します。

   OpenSSL などのユーティリティを使用するには、コマンドウィンドウを開き、次のように入力します。

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. 秘密鍵を保護するためのパスワードを入力するよう求められたら、パスワードを入力します。

   パスワードには少なくとも 12 文字を含め、文字には大文字と小文字の ASCII 文字と数字を混在させる必要があります。
1. OpenSSL を使用して強力なパスワードを生成するには、コマンドウィンドウを開き、次のように入力します。

   ```shell
   openssl rand -base64 8
   ```

1. 証明書署名要求 (CSR) を生成します。

   OpenSSL を使用して CSR を生成するには、コマンドウィンドウを開き、次のように入力します。

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. 証明書に自己署名し、任意の期間を入力します。

   次の例では、20 年間の有効期限が設定されています。

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. 自己署名証明書を PKCS#12 ファイルに変換します。

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   自己署名証明書を使用して、iOSアプリに署名できます。

1. PFX ファイルとパスワードの場所を更新します。
1. Xcode でアプリケーションを構築する前に、次に移動します。  **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** 次のコマンドを実行スクリプトに追加します。

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. 実行 [!DNL machotools] アプリの Publisher ID ハッシュ値を生成するために使用します。

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. 新しい DRM ポリシーを作成するか、既存のポリシーを更新して、返された Publisher ID ハッシュ値を含めます。
1. の使用 [!DNL AdobePolicyManager.jar]、返された Publisher ID ハッシュ値、オプションのアプリ ID、含まれるに最小バージョン属性と最大バージョン属性を含めるために、新しい DRM ポリシーを作成（既存のポリシーを更新）します [!DNL flashaccess-tools.properties] ファイル。

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. 新しい DRM ポリシーを使用してコンテンツをパッケージ化し、iOSアプリで許可リストに登録されているコンテンツの再生を確認します。
