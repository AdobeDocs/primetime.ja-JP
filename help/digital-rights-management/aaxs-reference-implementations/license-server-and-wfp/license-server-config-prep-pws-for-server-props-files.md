---
title: サーバープロパティファイルのパスワードの準備
description: サーバープロパティファイルのパスワードの準備
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# サーバープロパティファイルのパスワードの準備 {#preparing-passwords-for-the-server-properties-files}

秘密鍵証明書のパスワードのセキュリティを確保するために、パスワードを [!DNL flashaccess-refimpl.properties] または [!DNL flashaccess-refimpl-packager.properties] ファイル。

提供されている ANT スクリプトを使用してツールを実行するには、次の手順に従います。

* に移動します。 *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* 次を確認します。 `sdkdir` プロパティ： [!DNL build-refimpl.xml] は、AdobeAccess SDK を含むディレクトリを指します。
* ANT を使用して次のコマンドを実行します。

  ```
      ant -f build-refimpl.xml
  ```

* プロンプトが表示されたら、資格情報のパスワードを入力します。

Java を使用してツールを実行するには：

* に移動します。 *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* コマンドプロンプトで、次のコマンドを入力します。

* Windows の場合：

  ```
  java -classpath path_to_adobe-flashaccess-sdk.jar;.  
  com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

* Linux の場合：

  ```
      java -classpath path_to_adobe-flashaccess-sdk.jar;.  
      com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

ユーティリティは暗号化されたパスワードを出力します。このパスワードは.properties ファイルにコピーする必要があります。

>[!NOTE]
>
>参照実装で提供されるパスワードスクランブリングユーティリティを使用してエンコードされたパスワードは、Adobe Access Server for Protected Streaming では機能しません。
