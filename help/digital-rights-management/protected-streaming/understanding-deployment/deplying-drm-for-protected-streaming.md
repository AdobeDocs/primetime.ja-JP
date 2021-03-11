---
title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのデプロイ
description: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのデプロイ
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# 保護されたストリーミング用のAdobe PrimetimeDRMサーバーの展開{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

保護ストリーミング用のAdobe PrimetimeDRMサーバーを配備する前に、要件のトピックに記載されているJavaおよびTomcatのバージョンをインストールしておく必要があります。

保護されたストリーミング用のPrimetime DRMサーバーパッケージには[!DNL flashaccesserver.war]が含まれています。 次の場合：

* このWARファイルをデプロイするには、Tomcatの[!DNL webapps]ディレクトリにコピーする必要があります。
* WARファイルを以前にデプロイした場合は、パック解除されたWARディレクトリ（Tomcatの[!DNL webapps]ディレクトリの[!DNL flashaccessserver]）を削除する必要があります。

* TomcatがWARファイルを開くのを防ぐには、Tomcatの[!DNL conf]ディレクトリで[!DNL server.xml]ファイルを編集し、`unpackWARs`属性を`false`に設定して設定します。

>[!NOTE]
>
>システムのクラスパスに[!DNL commons-logging.jar]を含めるようにTomcatを設定した場合（保護ストリーミング用のPrimetime DRMサーバーには不要）、Log4Jを使用するようにTomcatのコモンズログを設定する必要があります。

サーバは、最適なパフォーマンスを得るために、オプションでプラットフォーム固有のライブラリ（Microsoft Windowsの場合は[!DNL jsafe.dll]、Linuxの場合は[!DNL libjsafe.so]）を使用します。 使用しているプラットフォームに適したライブラリを&#x200B;[!DNL thirdparty/cryptoj/]*プラットフォーム*&#x200B;から、Linuxの`PATH`環境変数または`LD_LIBRARY_PATH`で指定された場所にコピーできます。

>[!NOTE]
>
>64ビット版は、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。 それ以外の場合は、32ビットバージョンを使用する必要があります。

