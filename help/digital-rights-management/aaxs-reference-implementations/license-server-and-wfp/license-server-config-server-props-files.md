---
title: サーバーのプロパティファイル
description: サーバーのプロパティファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# サーバーのプロパティファイル {#server-properties-files}

サーバには 2 つの設定ファイルが必要です。1 つはライセンスサーバ用、もう 1 つはパッケージャ用です。 両方のファイルをクラスパスに配置する必要があります。 プロパティファイルには、Adobeが発行した資格情報の場所が含まれます。 これらの資格情報は、.pfx ファイルおよびパスワードとして指定するか、HSM に保存されている秘密鍵証明書のエイリアスとパスワードを指定することで指定できます。

各パラメーターの具体的な値と使用方法の詳細については、プロパティファイルを参照してください。 サンプルのプロパティファイルは、参照実装 (Reference Implementation\Server\resources) の「resources」ディレクトリにあります。

秘密鍵証明書のパスワードのセキュリティを確保するために、flashaccess-refimpl.properties または flashaccess-refimpl-packager.properties ファイルに入力する前にパスワードを暗号化するツール (ScranbleUtil.class) が提供されます。

秘密鍵証明書のパスワードを適切に準備するには、次の手順を実行します。

1. に移動します。 [!DNL Reference Implementation\Server\refimpl\scrambler].
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
>前の例では、区切り文字にセミコロン (;) を使用します。 Microsoft Windows 以外のプラットフォームでは、区切り文字にコロン (:) を使用します。

ユーティリティは暗号化されたパスワードを出力します。このパスワードは、 [!DNL .properties] ファイル。
