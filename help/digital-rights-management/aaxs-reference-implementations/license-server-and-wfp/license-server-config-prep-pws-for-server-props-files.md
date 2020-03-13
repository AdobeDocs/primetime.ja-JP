---
seo-title: サーバープロパティファイルのパスワードの準備
title: サーバープロパティファイルのパスワードの準備
uuid: 2d876eb0-b1a5-4c30-ae96-0a22f6a03910
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# サーバープロパティファイルのパスワードの準備 {#preparing-passwords-for-the-server-properties-files}

秘密鍵証明書のパスワードを確実にセキュリティで保護するため、またはファイルに入力する前にパスワードを暗号化するツールが [!DNL flashaccess-refimpl.properties] 提供さ [!DNL flashaccess-refimpl-packager.properties] れます。

提供されたANTスクリプトを使用してツールを実行するには：

* 移動先 *`<Reference Implementation Server Path>`*[!DNL \refimpl]

* のプロパティ `sdkdir` が、Adobe Access SDKを [!DNL build-refimpl.xml] 含むディレクトリを指していることを確認します。
* ANTを使用して次のコマンドを実行します。

   ```
       ant -f build-refimpl.xml
   ```

* プロンプトが表示されたら、秘密鍵証明書のパスワードを入力します

Javaを使用してツールを実行するには：

* 次の場所に移 *`<Reference Implementation Server Path>`*&#x200B;動\ [!DNL scrambler]

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

このユーティリティは、暗号化されたパスワードを出力します。このパスワードは.propertiesファイルにコピーする必要があります。

>[!NOTE]
>
>参照実装と共に提供されるパスワードスクランブルユーティリティを使用してエンコードされたパスワードは、保護されたストリーミング用のAdobe Access Serverでは機能しません。
