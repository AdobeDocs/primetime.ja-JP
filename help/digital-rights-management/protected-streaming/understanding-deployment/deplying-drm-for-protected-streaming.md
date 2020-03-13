---
seo-title: 保護されたストリーミング用のAdobe Primetime DRMサーバーのデプロイ
title: 保護されたストリーミング用のAdobe Primetime DRMサーバーのデプロイ
uuid: 83ef8237-0026-4677-b42b-ea4b6de19630
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 保護されたストリーミング用のAdobe Primetime DRMサーバーのデプロイ{#deploying-the-adobe-primetime-drm-server-for-protected-streaming}

Adobe Primetime DRM Server for Protected Streamingをデプロイする前に、要件のトピックに記載されているJavaおよびTomcatのバージョンをインストールしておく必要があります。

保護されたストリーミング用のPrimetime DRMサーバーパッケージには、が含まれていま [!DNL flashaccesserver.war]す。 次の場合：

* このWARファイルをデプロイするには、Tomcatのディレクトリにコピーする必要があり [!DNL webapps] ます。
* WARファイルを以前にデプロイした場合は、（Tomcatのディレクトリ内の）展開済みのWARディレ [!DNL flashaccessserver] クトリを削除する必要が [!DNL webapps] あります。

* TomcatがWARファイルを展開しないようにするには、Tomcatのディレ [!DNL server.xml] クトリでファイルを編集し、に設 [!DNL conf] 定して属 `unpackWARs` 性を設定してください `false`。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>Tomcatをシステムクラスパスに含めるように設定し [!DNL commons-logging.jar] た場合（Primetime DRMサーバーで保護ストリーミングを行う場合は不要）、Log4Jを使用するようにコモンズログを設定する必要があります。

サーバは、最適なパフォーマンスを得るために、(Microsoft Windows [!DNL jsafe.dll] またはLinuxで)プラットフォー [!DNL libjsafe.so] ム固有のライブラリを使用します。 プラットフォームに適したライブラリを、環境変数 [!DNL thirdparty/cryptoj/]*または&#x200B;*Linuxで指定された場所にプラットフォーム`PATH`からコピー`LD_LIBRARY_PATH`できます。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>64ビット版は、オペレーティングシステムとJDKの両方が64ビットをサポートしている場合にのみ使用してください。 それ以外の場合は、32ビットバージョンを使用する必要があります。

