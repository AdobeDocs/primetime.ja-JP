---
seo-title: サーバープロパティファイル
title: サーバープロパティファイル
uuid: 3d3a0ee3-009f-4d62-9587-7e487ecdcafd
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# サーバープロパティファイル {#server-properties-files}

サーバーには、ライセンスサーバー用とパッケージャー用の2つの設定ファイルが必要です。 両方のファイルをクラスパスに配置する必要があります。 プロパティファイルには、アドビが発行した秘密鍵証明書の場所が含まれます。 これらの秘密鍵証明書は、.pfxファイルとパスワードとして指定するか、HSMに保存されている秘密鍵証明書のエイリアスとパスワードを指定します。

各パラメーターの具体的な値と使用方法の詳細については、プロパティファイルを参照してください。 サンプルのプロパティファイルは、リファレンス実装の「resources」ディレクトリ(Reference Implementation\Server\resources)にあります。

秘密鍵証明書のパスワードを確実にセキュリティで保護するために、flashaccess-refimpl.propertiesまたはflashaccess-refimpl-packager.propertiesファイルにパスワードを入力する前に、パスワードを暗号化するツール(ScrambleUtil.class)が提供されます。

秘密鍵証明書のパスワードを適切に準備するには：

1. に移動しま [!DNL Reference Implementation\Server\refimpl\scrambler]す。
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

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>前述の例では、セミコロン(;)を区切り文字として使用しています。 Microsoft Windows以外のプラットフォームでは、コロン(:)を区切り文字として使用します。

このユーティリティは、暗号化されたパスワードを出力します。このパスワードはファイルにコピーする必要が [!DNL .properties] あります。
