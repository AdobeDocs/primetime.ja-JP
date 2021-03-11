---
title: サーバープロパティファイルのパスワードの準備
description: サーバープロパティファイルのパスワードの準備
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# サーバープロパティファイル{#preparing-passwords-for-the-server-properties-files}のパスワードの準備

秘密鍵証明書のパスワードをセキュリティで保護するために、[!DNL flashaccess-refimpl.properties]または[!DNL flashaccess-refimpl-packager.properties]ファイルに入力する前にパスワードを暗号化するツールが提供されます。

提供されたANTスクリプトを使用してツールを実行するには：

* *`<Reference Implementation Server Path>`* [!DNL \refimpl]に移動

* [!DNL build-refimpl.xml]の`sdkdir`プロパティが、AdobeアクセスSDKを含むディレクトリを指していることを確認します
* ANTを使用して次のコマンドを実行します。

   ```
       ant -f build-refimpl.xml
   ```

* プロンプトが表示されたら、秘密鍵証明書のパスワードを入力します

Javaを使用してツールを実行するには：

* *`<Reference Implementation Server Path>`*\ [!DNL scrambler]に移動

* コマンドプロンプトで、次のコマンドを入力します。

* Windowsの場合：

   ```
   java -classpath path_to_adobe-flashaccess-sdk.jar;.  
   com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

* Linuxの場合：

   ```
       java -classpath path_to_adobe-flashaccess-sdk.jar;.  
       com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
   ```

このユーティリティは、暗号化されたパスワードを出力します。このパスワードを.propertiesファイルにコピーする必要があります。

>[!NOTE]
>
>リファレンス実装と共に提供されるパスワードスクランブリングユーティリティを使用してエンコードされたパスワードは、保護ストリーミング用Adobe Access Serverでは機能しません。
