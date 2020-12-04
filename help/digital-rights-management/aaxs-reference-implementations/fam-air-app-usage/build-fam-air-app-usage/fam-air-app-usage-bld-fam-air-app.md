---
seo-title: Flash AccessマネージャーAIRアプリケーションの構築
title: Flash AccessマネージャーAIRアプリケーションの構築
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Flash AccessマネージャーAIRアプリケーションの構築{#building-the-flash-access-manager-air-application}

ソースコードからFlash AccessマネージャーのAIRファイルを作成するには、マシンにFlexおよびAIR SDKがインストールされている必要があります。 アプリケーションをパッケージ化して実行する前に、MXMLコードを[!DNL amxmlc]コンパイラーを使用してSWFファイルにコンパイルする必要があります。 [!DNL amxmlc]コンパイラーは、Flex4以降のSDKの[!DNL bin]ディレクトリにあります。 必要に応じて、パス環境ー変数を設定して、FlexSDKのbinディレクトリを含めると、コマンドラインで簡単にユーティリティを実行できます。

Flash AccessマネージャーのAIRファイルを作成するには、次の手順を実行します。

1. コマンドシェルまたはターミナルを開き、Flash AccessマネージャーAIRアプリケーションのプロジェクトフォルダー（参照実装ディレクトリの[!DNL UI Tools\Flash Access Manager]）に移動します。
1. 次のコマンドを入力します。

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   [!DNL amxmlc]を実行すると、[!DNL FlashAccessManager.swf]が生成されます。この中には、アプリケーションのコンパイル済みコードが含まれています。

Adobe AIRSDKには、AIRアプリケーションをパッケージ化して証明書を生成するAIR Developer Tool(ADT)ユーティリティが含まれています。 AIRアプリケーションは、デジタル署名する必要があります。適切に署名されていない、またはまったく署名されていないアプリケーションをインストールすると、ユーザーに警告が表示されます。 コマンドラインを使用して証明書を生成するには、AIRアプリケーションと同じフォルダーにあるコンソールウィンドウを開き、次のように入力します。

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

*some_password*&#x200B;は任意のパスワードに置き換えてください。 数秒後、ADTは証明書の生成プロセスを完了し、新しい[!DNL testCert.pfx]ファイルをアプリケーションディレクトリに配置する必要があります。

次に、ADTを使用し、次のコマンドを使用して、アプリケーションを[!DNL .air]ファイルにパッケージ化します。

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

このコマンドは、[!DNL testCert.pfx]のキーファイルを使用して、アプリケーションをパッケージ化するようADTに指示します。 上の行では、アプリケーション全体を[!DNL FlashAccessManager.air]という名前のファイルにパッケージ化し、[!DNL FlashAccessManager-app.xml]と[!DNL FlashAccessManager.swf]のファイルとアセットディレクトリの画像を含めるようにADTを設定します。

この処理の一環として、新しい証明書ファイルに設定したパスワードの入力を求められます。 入力し、しばらく待ってください。[!DNL FlashAccessManager.air]ファイルがプロジェクトファイルと同じディレクトリに表示されます。
