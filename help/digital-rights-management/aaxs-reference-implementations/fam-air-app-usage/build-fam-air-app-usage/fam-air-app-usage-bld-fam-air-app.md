---
title: Flash AccessマネージャーAIRアプリケーションの構築
description: Flash AccessマネージャーAIRアプリケーションの構築
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Flash AccessマネージャーAIRアプリケーションの構築 {#building-the-flash-access-manager-air-application}

ソースコードからFlash AccessManager AIRファイルを構築するには、FlexとAIR SDK がコンピューターにインストールされている必要があります。 アプリケーションをパッケージ化して実行する前に、MXMLコードををを使用してSWFファイルにコンパイルする必要があります。 [!DNL amxmlc] コンパイラ。 The [!DNL amxmlc] コンパイラは、 [!DNL bin] Flex 4 以降の SDK のディレクトリ。 必要に応じて、 Flex SDK bin ディレクトリを含むようにパス環境変数を設定し、コマンドラインでユーティリティを簡単に実行できるようにします。

次の手順を実行して、Flash AccessマネージャーのAIRファイルを作成します。

1. コマンドシェルまたはターミナルを開き、Flash AccessManager AIRアプリケーションのプロジェクトフォルダーに移動します ( [!DNL UI Tools\Flash Access Manager] を参照してください )。
1. 次のコマンドを入力します。

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   実行中 [!DNL amxmlc] 生成する [!DNL FlashAccessManager.swf]：アプリケーションのコンパイル済みコードを含みます。

Adobe AIR SDK には、AIRアプリケーションをパッケージ化して証明書を生成するAIR Developer Tool(ADT) ユーティリティが含まれています。 AIRアプリケーションはデジタル署名を受ける必要があります。正しく署名されていない、またはまったく署名されていないアプリケーションをインストールすると、警告が表示されます。 コマンドラインを使用して証明書を生成するには、AIRアプリケーションと同じフォルダー内のコンソールウィンドウを開き、次のように入力します。

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

代用 *some_password* 選択したパスワードを使用します。 数秒後に、ADT が証明書の生成プロセスを完了し、新しい [!DNL testCert.pfx] ファイルを作成します。

次に、ADT を使用して、アプリケーションを [!DNL .air] ファイルを作成するには、次のコマンドを使用します。

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

このコマンドは、ADT に対し、 [!DNL testCert.pfx]. 上記の行で、アプリケーション全体をという名前のファイルにパッケージ化するように ADT を設定します。 [!DNL FlashAccessManager.air]、およびを使用してファイルをインクルードします。 [!DNL FlashAccessManager-app.xml] および [!DNL FlashAccessManager.swf] および画像を assets ディレクトリから取得します。

この処理の一環として、新しい証明書ファイルに設定したパスワードを求めるメッセージが表示されます。 入力し、しばらく待ってから、 [!DNL FlashAccessManager.air] ファイルは、プロジェクトファイルと同じディレクトリに存在する必要があります。
