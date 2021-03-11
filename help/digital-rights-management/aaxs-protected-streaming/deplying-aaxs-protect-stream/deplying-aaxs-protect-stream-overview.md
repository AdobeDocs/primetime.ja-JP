---
title: 保護ストリーミング用Adobe Access Serverの展開の概要
description: 保護ストリーミング用Adobe Access Serverの展開の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# 保護ストリーミング用Adobe Access Serverの展開の概要{#deploying-the-adobe-access-server-for-protected-streaming-overview}

保護ストリーミング用のAdobe Access Serverを展開する前に、「要件」の節に示すJavaおよびTomcatのバージョンがインストールされていることを確認してください。

保護ストリーミング用Adobe Access Serverパッケージには[!DNL flashaccesserver.war]が含まれます。 このWARファイルを配備するには、Tomcatの[!DNL webapps]ディレクトリにファイルをコピーします。 WARファイルを以前にデプロイした場合は、パック解除されたWARディレクトリ（Tomcatの[!DNL webapps]ディレクトリの[!DNL flashaccessserver]）を手動で削除する必要があります。 TomcatがWARファイルを開くのを防ぐには、Tomcatの[!DNL conf]ディレクトリで[!DNL server.xml]ファイルを編集し、`unpackWARs`属性を`false`に設定します。

>[!NOTE]
>
>Tomcatを設定して、[!DNL commons-logging.jar]をSystemクラスパスに含める場合(Protected StreamingにはAdobe Access Serverは不要)、Log4Jを使用するようにCommons-loggingを設定する必要があります。

サーバは、最適なパフォーマンスを得るために、オプションでプラットフォーム固有のライブラリ（Microsoft Windowsの場合は[!DNL jsafe.dll]、Linuxの場合は[!DNL libjsafe.so]）を使用します。 使用しているプラットフォームに適したライブラリを&#x200B;[!DNL thirdparty/cryptoj/]*プラットフォーム*&#x200B;から`PATH`環境変数（Linuxでは`LD_LIBRARY_PATH`）で指定された場所にコピーします。

>[!NOTE]
>
>64ビットバージョンは、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。それ以外の場合は、32ビットバージョンを使用してください。

