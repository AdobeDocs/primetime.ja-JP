---
seo-title: 保護ストリーミング用Adobe Access Serverの展開の概要
title: 保護ストリーミング用Adobe Access Serverの展開の概要
uuid: 48a7e452-520a-4ff8-97e9-11210221256d
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# 保護ストリーミング用Adobe Access Serverの展開の概要 {#deploying-the-adobe-access-server-for-protected-streaming-overview}

保護ストリーミング用のAdobe Access Serverを展開する前に、「要件」の節に示すJavaおよびTomcatのバージョンがインストールされていることを確認してください。

Protected Streaming用のAdobe Access Serverパッケージには、が含まれ [!DNL flashaccesserver.war]ます。 このWARファイルを配備するには、Tomcatの [!DNL webapps] ディレクトリにファイルをコピーします。 WARファイルを以前にデプロイした場合は、（Tomcatのディレクトリにある）アンパックしたWARディレクトリ [!DNL flashaccessserver] を手動で削除する必要があり [!DNL webapps] ます。 TomcatがWARファイルを開くのを防ぐには、Tomcatの [!DNL server.xml] ディレクトリで [!DNL conf] ファイルを編集し、 `unpackWARs` 属性をに設定し `false`ます。

>[!NOTE]
>
>システムクラスパスに含めるようにTomcatを設定した場合(Protected Streaming [!DNL commons-logging.jar] にはAdobe Access Serverが不要)、Log4Jを使用するようにCommons-loggingを設定する必要があります。

最適なパフォーマンスを得るために、サーバはオプションでプラットフォーム固有 [!DNL jsafe.dll] のライブラリ(Microsoft WindowsまたはLinux [!DNL libjsafe.so] )を使用します。 プラットフォームに適したライブラリを、プラットフォーム [!DNL thirdparty/cryptoj/]**から、`PATH`環境変数(またはLinux`LD_LIBRARY_PATH`)で指定された場所にコピーします。

>[!NOTE]
>
>64ビットバージョンは、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。それ以外の場合は、32ビットバージョンを使用してください。

