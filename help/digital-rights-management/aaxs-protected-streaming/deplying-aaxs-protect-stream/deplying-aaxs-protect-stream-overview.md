---
title: 保護されたストリーミング用Adobe Access Serverのデプロイの概要
description: 保護されたストリーミング用Adobe Access Serverのデプロイの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# 保護されたストリーミング用Adobe Access Serverのデプロイの概要 {#deploying-the-adobe-access-server-for-protected-streaming-overview}

保護されたストリーミング用のAdobe Access Serverをデプロイする前に、要件の節に記載されている Java および Tomcat のバージョンがインストールされていることを確認してください。

Adobe Access Server for Protected Streaming パッケージには、以下が含まれています。 [!DNL flashaccesserver.war]. この WAR ファイルをデプロイするには、Tomcat の [!DNL webapps] ディレクトリ。 WAR ファイルを既に展開している場合は、パック解除された WAR ディレクトリ ( [!DNL flashaccessserver] Tomcat の [!DNL webapps] ディレクトリ ) に書き込まれます。 Tomcat が WAR ファイルを展開しないようにするには、 [!DNL server.xml] Tomcat のファイル [!DNL conf] ディレクトリに移動し、 `unpackWARs` 属性 `false`.

>[!NOTE]
>
>Tomcat が [!DNL commons-logging.jar] System クラスパス (Adobe Access Server for Protected Streaming では不要 ) で、Log4J を使用するように commons-logging を設定する必要があります。

サーバーは、必要に応じて、プラットフォーム固有のライブラリ ( [!DNL jsafe.dll] (Microsoft Windows または [!DNL libjsafe.so] （Linux の場合）最適なパフォーマンスを得るために使用します。 プラットフォームに適したライブラリを次の場所からコピーします。 [!DNL thirdparty/cryptoj/]*platform* を `PATH` 環境変数 ( または `LD_LIBRARY_PATH` （Linux の場合）。

>[!NOTE]
>
>64 ビットバージョンは、オペレーティングシステムと JDK の両方が 64 ビットをサポートしている場合にのみ使用し、それ以外の場合は 32 ビットバージョンを使用します。
