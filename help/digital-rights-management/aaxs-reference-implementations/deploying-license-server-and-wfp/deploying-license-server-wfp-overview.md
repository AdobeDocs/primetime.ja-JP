---
seo-title: ライセンスサーバーと監視フォルダーパッケージャーの展開の概要
title: ライセンスサーバーと監視フォルダーパッケージャーの展開の概要
uuid: 4b71f2f4-f971-4382-ae41-171f7dfdfe21
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ライセンスサーバーと監視フォルダーパッケージャーの展開の概要 {#deploying-the-license-server-and-watched-folder-packager-overview}

ライセンスサーバーのWARファイルをTomcatのディレクトリにコピー [!DNL webapps] します。 WARファイルを以前にデプロイした場合は、パック解除されたWARディレクトリ( 、 、およびTomcatのデ [!DNL flashaccess]ィレクト [!DNL edcws]リ)を手 [!DNL flashaccess-packager] 動で削除する必要が [!DNL webapps] あります。 TomcatがWARファイルを展開しないようにするには、Tomcatのconf [!DNL server.xml] ディレクトリでファイルを編集し、属性をに設 `unpackWARs` 定しま `false`す。

プロパティファイル( [!DNL flashaccess-refimpl.properties])は、サーバーがプロパティを読み込むためのクラスパス上に存在する必要があります。 このファイルをディレクトリにコピーし、適切な値でファイルを更新します。 Tomcatのディレ [!DNL catalina.properties] クトリ内のファイルを編 [!DNL conf] 集し、を含むディレクトリをプロパテ [!DNL flashaccess-refimpl.properties] ィに追加 `shared.loader` します。 ログを [!DNL log4j.xml] 設定するファイルも、クラスパス上に存在する必要があります(例 [!DNL resources\log4j.xml] を参照)。

参照実装サーバーは、複数の証明書ファイル、ポリシーファイル、その他のリソースを使用します。 これらのファイルはすべて1つのリソースフォルダーに格納されます。 デフォルトでは、リソースフォルダは [!DNL C:\flashaccess-server-resources]ですが、この場所はで変更できま [!DNL flashaccess-refimpl.properties]す。 サーバーを起動する前に、必要なすべてのリソースをこの場所にコピーしてください。

Tomcatとライセンスサーバーを起動するには、Tomcatのデ `catalina.bat start` ィレクトリからを実行 [!DNL bin] します。
