---
seo-title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのデプロイ
title: 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのデプロイ
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# 保護されたストリーミング用のAdobe PrimetimeDRMサーバーのデプロイ{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

保護ストリーミング用のAdobe PrimetimeDRMサーバーを配備する前に、要件のトピックに記載されているJavaおよびTomcatのバージョンをインストールしておく必要があります。

保護されたストリーミング用のPrimetime DRMサーバーには、が含まれ [!DNL flashaccesserver.war]ます。 次の場合：

* このWARファイルをデプロイするには、Tomcatの [!DNL webapps] ディレクトリにコピーする必要があります。
* WARファイルを以前に展開している場合は、（ Tomcatのディレクトリ内の）パック解除されたWARディレクトリ [!DNL flashaccessserver] を削除する必要があり [!DNL webapps] ます。

* WARファイルの開梱をTomcatで防ぐには、Tomcatの [!DNL server.xml] ディレクトリでファイルを編集し、に設定して [!DNL conf] 属性を設定し `unpackWARs``false`ます。

>[!NOTE]
>
>システムクラスパスに含めるよう [!DNL commons-logging.jar] にTomcatを設定した場合（Primetime DRMサーバーで保護ストリーミングを行う場合は不要）、Log4Jを使用するようにコモンズログを設定する必要があります。

サーバは、最適なパフォーマンスを得るために、オプションでプラットフォーム固有のライブラリ(Microsoft Windows [!DNL jsafe.dll] またはLinux [!DNL libjsafe.so] 上)を使用します。 プラットフォームに適したライブラリを、プラットフォーム [!DNL thirdparty/cryptoj/]**から、`PATH`環境変数またはLinuxで指定された場所にコピー`LD_LIBRARY_PATH`できます。

>[!NOTE]
>
>64ビット版は、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。 それ以外の場合は、32ビットバージョンを使用する必要があります。

