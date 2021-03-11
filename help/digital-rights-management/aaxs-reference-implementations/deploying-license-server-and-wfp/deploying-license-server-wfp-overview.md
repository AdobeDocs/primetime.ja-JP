---
title: ライセンスサーバーと監視フォルダーパッケージャーの展開の概要
description: ライセンスサーバーと監視フォルダーパッケージャーの展開の概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# ライセンスサーバーと監視フォルダーパッケージャーの展開の概要{#deploying-the-license-server-and-watched-folder-packager-overview}

ライセンスサーバーのWARファイルをTomcatの[!DNL webapps]ディレクトリにコピーします。 WARファイルを以前にデプロイした場合は、Tomcatの[!DNL webapps]ディレクトリ内にある、アンパックしたWARディレクトリ([!DNL flashaccess]、[!DNL edcws]、[!DNL flashaccess-packager])を手動で削除する必要があります。 TomcatがWARファイルを開くのを防ぐには、Tomcatのconfディレクトリで[!DNL server.xml]ファイルを編集し、`unpackWARs`属性を`false`に設定します。

プロパティファイル([!DNL flashaccess-refimpl.properties])は、サーバーがプロパティを読み込むためのクラスパス上に存在する必要があります。 このファイルをディレクトリにコピーし、適切な値でファイルを更新します。 Tomcatの[!DNL conf]ディレクトリで[!DNL catalina.properties]ファイルを編集し、[!DNL flashaccess-refimpl.properties]を含むディレクトリを`shared.loader`プロパティに追加します。 ログを設定するための[!DNL log4j.xml]ファイルは、クラスパス上にも存在する必要があります（例については[!DNL resources\log4j.xml]を参照）。

参照実装サーバーは、複数の証明書ファイル、ポリシーファイル、その他のリソースを使用します。 これらのファイルはすべて1つのリソースフォルダーに格納されます。 デフォルトでは、リソースフォルダーは[!DNL C:\flashaccess-server-resources]ですが、この場所は[!DNL flashaccess-refimpl.properties]で変更できます。 サーバーを起動する前に、必要なすべてのリソースをこの場所にコピーしてください。

Tomcatとライセンスサーバを開始するには、Tomcatの[!DNL bin]ディレクトリから`catalina.bat start`を実行します。
