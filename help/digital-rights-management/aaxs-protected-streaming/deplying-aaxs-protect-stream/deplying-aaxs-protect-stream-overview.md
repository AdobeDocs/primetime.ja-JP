---
seo-title: 保護されたストリーミング用のAdobe Access Serverの導入の概要
title: 保護されたストリーミング用のAdobe Access Serverの導入の概要
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 保護されたストリーミング用のAdobe Access Serverの導入の概要 {#deploying-the-adobe-access-server-for-protected-streaming-overview}

保護されたストリーミング用のAdobe Access Serverを展開する前に、「要件」の節に示すJavaおよびTomcatのバージョンがインストールされていることを確認してください。

Protected Streaming用のAdobe Access Serverパッケージには、が含まれていま [!DNL flashaccesserver.war]す。 このWARファイルをデプロイするには、Tomcatのディレクトリにコピーし [!DNL webapps] ます。 WARファイルを以前にデプロイした場合は、（Tomcatのディレクトリ内の）アンパックされたWARディレクトリを手動で削除す [!DNL flashaccessserver] る必要がある場合が [!DNL webapps] あります。 TomcatがWARファイルを展開しないようにするには、Tomcatのデ [!DNL server.xml] ィレクトリでファイルを編集 [!DNL conf] し、属性をに設 `unpackWARs` 定します `false`。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Tomcatをシステムクラスパスに含めるように設定し [!DNL commons-logging.jar] た場合（Adobe Access Server for Protected Streamingには不要）、Log4Jを使用するようにCommons-loggingを設定する必要があります。

サーバは、最適なパフォーマンスを得るために、(Microsoft Windowsま [!DNL jsafe.dll] たはLinuxで)プラットフォー [!DNL libjsafe.so] ム固有のライブラリを使用します。 プラットフォームに適したライブラリを、環境変 [!DNL thirdparty/cryptoj/]*数&#x200B;*（またはLinux）で指定された場`PATH`所にプラットフォームに`LD_LIBRARY_PATH`コピーします。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>64ビットバージョンは、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用し、それ以外の場合は32ビットバージョンを使用します。

