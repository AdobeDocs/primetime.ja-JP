---
seo-title: Flash Access Manager AIRアプリケーションの構築
title: Flash Access Manager AIRアプリケーションの構築
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Flash Access Manager AIRアプリケーションの構築 {#building-the-flash-access-manager-air-application}

ソースコードからFlash Access Manager AIRファイルを構築するには、FlexおよびAIR SDKがマシンにインストールされている必要があります。 アプリケーションをパッケージ化して実行する前に、コンパイラーを使用してMXMLコードをSWFファイルにコンパイルする必要があ [!DNL amxmlc] ります。 コンパ [!DNL amxmlc] イラは、Flex 4以降のSDK [!DNL bin] のディレクトリにあります。 必要に応じて、Flex SDK binディレクトリを含めるようにpath環境変数を設定し、コマンドラインでユーティリティをより簡単に実行できるようにします。

次の手順を使用して、Flash Access Manager AIRファイルを構築します。

1. コマンドシェルまたはターミナルを開き、Flash Access Manager AIRアプリケーションのプロジェクトフォルダ(Reference Implementationデ [!DNL UI Tools\Flash Access Manager] ィレクトリ内)に移動します。
1. 次のコマンドを入力します。

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   を実行する [!DNL amxmlc] と、ア [!DNL FlashAccessManager.swf]プリケーションのコンパイル済みコードが含まれるが、

Adobe AIR SDKには、AIRアプリケーションをパッケージ化し、証明書を生成するAIR Developer Tool(ADT)ユーティリティが含まれています。 AIRアプリケーションは、デジタル署名が必要です。適切に署名されていない、またはまったく署名されていないアプリケーションをインストールすると、ユーザーに警告が表示されます。 コマンドラインを使用して証明書を生成するには、AIRアプリケーションと同じフォルダーにあるコンソールウィンドウを開き、次のように入力します。

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

some_password *は* 、任意のパスワードに置き換えます。 数秒後、ADTは証明書の生成プロセスを完了し、アプリケーションディレクトリに新しいフ [!DNL testCert.pfx] ァイルを作成する必要があります。

次に、ADTを使用し、次のコマンドを使用して、アプリケーシ [!DNL .air] ョンをファイルにパッケージ化します。

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

このコマンドは、ADTに対し、のキーファイルを使用してアプリケーションをパッケージ化するよう指示しま [!DNL testCert.pfx]す。 上の行では、アプリケーション全体をという名前のファイルにパッケージ化し、アセットディレク [!DNL FlashAccessManager.air]トリのファイルと画像を含め [!DNL FlashAccessManager-app.xml] るよ [!DNL FlashAccessManager.swf] うにADTを設定しています。

この処理の一環として、新しい証明書ファイルに設定したパスワードの入力を求められます。 ファイルを入力し、しばらく待つと、プロジ [!DNL FlashAccessManager.air] ェクトファイルと同じディレクトリにファイルが表示されます。
