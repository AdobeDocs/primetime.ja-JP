---
title: ライセンスサーバーと監視フォルダーパッケージャのデプロイの概要
description: ライセンスサーバーと監視フォルダーパッケージャのデプロイの概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# ライセンスサーバーと監視フォルダーパッケージャのデプロイの概要 {#deploying-the-license-server-and-watched-folder-packager-overview}

ライセンスサーバーの WAR ファイルを Tomcat の [!DNL webapps] ディレクトリ。 WAR ファイルを既に展開している場合は、パック解除された WAR ディレクトリ ( [!DNL flashaccess], [!DNL edcws]、および [!DNL flashaccess-packager] Tomcat の [!DNL webapps] ディレクトリ ) に書き込まれます。 Tomcat が WAR ファイルを展開しないようにするには、 [!DNL server.xml] Tomcat の conf ディレクトリ内のファイルを参照し、 `unpackWARs` 属性 `false`.

プロパティファイル ( [!DNL flashaccess-refimpl.properties]) は、サーバーがプロパティを読み込むためのクラスパス上に存在する必要があります。 このファイルをディレクトリにコピーし、適切な値でファイルを更新します。 を編集します。 [!DNL catalina.properties] Tomcat のファイル [!DNL conf] ディレクトリを開き、次のディレクトリを含むディレクトリを追加します。 [!DNL flashaccess-refimpl.properties] から `shared.loader` プロパティ。 The [!DNL log4j.xml] ログを構成するファイルもクラスパス上にある必要があります ( [!DNL resources\log4j.xml] 例を示します )。

参照実装サーバーは、複数の証明書ファイル、ポリシーファイル、およびその他のリソースを使用します。 これらのファイルはすべて 1 つのリソースフォルダに格納されます。 デフォルトでは、リソースフォルダーは [!DNL C:\flashaccess-server-resources]を変更できますが、この場所はで変更できます。 [!DNL flashaccess-refimpl.properties]. サーバーを起動する前に、必要なリソースをすべてこの場所にコピーしてください。

Tomcat とライセンスサーバーを起動するには、次のコマンドを実行します。 `catalina.bat start` Tomcat の [!DNL bin] ディレクトリ。
