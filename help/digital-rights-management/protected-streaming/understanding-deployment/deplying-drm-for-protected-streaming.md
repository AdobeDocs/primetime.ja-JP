---
title: 保護されたストリーミング用のAdobe Primetime DRM サーバーのデプロイ
description: 保護されたストリーミング用のAdobe Primetime DRM サーバーのデプロイ
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# 保護されたストリーミング用のAdobe Primetime DRM サーバーのデプロイ{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

保護されたストリーミング用のAdobe Primetime DRM サーバーをデプロイする前に、要件のトピックに記載されている Java および Tomcat のバージョンをインストールしておく必要があります。

保護されたストリーミング用の Primetime DRM サーバーパッケージには、以下が含まれます。 [!DNL flashaccesserver.war]. 次の場合：

* この WAR ファイルをデプロイするには、Tomcat の [!DNL webapps] ディレクトリ。
* 以前に WAR ファイルを展開しておいた場合は、WAR の展開ディレクトリ ( [!DNL flashaccessserver] Tomcat の [!DNL webapps] ディレクトリ ) に書き込まれます。

* Tomcat が WAR ファイルを開くのを防ぐには、 [!DNL server.xml] Tomcat のファイル [!DNL conf] ディレクトリを作成し、 `unpackWARs` 属性を次のように設定します。 `false`.

>[!NOTE]
>
>Tomcat が [!DNL commons-logging.jar] System クラスパス（Primetime DRM Server for Protected Streaming では不要）で、Log4J を使用するように commons-logging を設定する必要があります。

サーバーは、必要に応じて、プラットフォーム固有のライブラリ ( [!DNL jsafe.dll] (Microsoft Windows または [!DNL libjsafe.so] Linux 上で最適なパフォーマンスを得るために使用します。 次の場所から、プラットフォームに適したライブラリをコピーできます。 [!DNL thirdparty/cryptoj/]*platform* を `PATH` 環境変数または `LD_LIBRARY_PATH` （Linux の場合）

>[!NOTE]
>
>オペレーティングシステムと JDK の両方が 64 ビットをサポートしている場合にのみ、64 ビットバージョンを使用してください。 それ以外の場合は、32 ビットバージョンを使用する必要があります。
