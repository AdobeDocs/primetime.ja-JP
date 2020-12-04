---
seo-title: サーバーのプロパティファイル
title: サーバーのプロパティファイル
uuid: 3d3a0ee3-009f-4d62-9587-7e487ecdcafd
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# サーバーのプロパティファイル{#server-properties-files}

サーバーには、ライセンスサーバー用とパッケージャー用の2つの設定ファイルが必要です。 両方のファイルをクラスパスに配置する必要があります。 プロパティファイルには、Adobeが発行する秘密鍵証明書の場所が含まれます。 これらの秘密鍵証明書は、.pfxファイルとパスワードとして指定するか、HSMに保存されている秘密鍵証明書のエイリアスとパスワードを指定して指定できます。

各パラメーターの具体的な値と使用方法の詳細については、プロパティファイルを参照してください。 サンプルのプロパティファイルは、リファレンス実装の「resources」ディレクトリ(リファレンスImplementation\Server\resources)にあります。

秘密鍵証明書のパスワードをセキュリティで保護するために、flashaccess-refimpl.propertiesファイルまたはflashaccess-refimpl-packager.propertiesファイルに入力する前に、パスワードを暗号化するツール(ScrambleUtil.class)が提供されます。

秘密鍵証明書のパスワードを適切に準備するには：

1. [!DNL Reference Implementation\Server\refimpl\scrambler]に移動します。
1. コマンドプロンプトで、次のコマンドを入力します。

   ```
   java -classpath  
   <i class="+ topic ph hi-d="" i "="">
   path_to_adobe-flashaccess-sdk.jar.; 
        com.adobe.flashaccess.refimpl.util.ScrambleUtil " 
   <i class="+ topic ph hi-d="" i "="">
   your_pfx_password" 
   </i class="+ topic> 
   </i class="+ topic>
   ```

>[!NOTE]
>
>前の例では、セミコロン(;)を区切り文字として使用しています。 Microsoft Windows以外のプラットフォームでは、区切り文字にコロン(:)を使用します。

このユーティリティは、暗号化されたパスワードを出力します。[!DNL .properties]ファイルにコピーする必要があります。
