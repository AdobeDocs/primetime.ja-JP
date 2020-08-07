---
seo-title: データベースの設定とJNDIデータソースの設定
title: データベースの設定とJNDIデータソースの設定
uuid: 1326523f-c053-4169-a934-1b2d3907b1f4
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# データベースの設定とJNDIデータソースの設定 {#setting-up-the-database-and-configuring-the-jndi-datasource}

参照実装のライセンスサーバーでは、次の機能をサポートするデータベースが必要です。

* ユーザー認証
* 使用モデルデモビジネスルール
* メタデータ変換
* ドメインのサポート

匿名ライセンスの取得には、データベースを実行する必要はありません。

>[!NOTE]
>
>この節の説明は、Microsoft Windowsプラットフォーム向けです。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQLのドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQL 5.1.34をインストールして設定する必要があります。

1. MySQLインストーラーを実行します(DVDのThird Party\MySQL\Installer\5.1フォルダーにあります)。
1. インストール手順の最後に、構成ウィザード **[!UICONTROL Configure MySQL Server Now]** の開始を確認します。 デフォルト設定を使用するか、テスト用に特定の設定を選択します。ただし、5番目の画面では、またはを選択し **[!UICONTROL Online Transaction Processing (OLTP)]** て、最大接続数を入力する必要があり **[!UICONTROL Manual Setting]** ます。

1. rootパスワードをメモしておきます。
1. MySQLを再インストールする必要がある場合は、次の手順に従って、後でサーバーを起動する際の問題を回避します。

   * フォルダー *システムドライブを削除します。*[!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * 古いMySQLインストールフォルダーを削除します。例えば、 *システムドライブ：*[!DNL \Program Files\MySQL\MySQL Server 5.1].

次に、MySQL JDBC Driver 5.1.7をインストールする必要があります。これを行うには、 [!DNL mysql-connector-java-5.1.7-bin.jar] (DVD上の [!DNL Third Party\MySQL\Installer\5.1] フォルダーにある)をTomcatサーバーのlibディレクトリにコピーします。 [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7はTomcat 6.0で動作します。古いバージョンのTomcatはサポートされていません。

データベース・データベースを設定し、データベースにサンプル・データを入力して、サンプル・スキーマを設定します。 これを行うには、次の手順を実行します。

1. / **[!UICONTROL Window's Start Menu]** / **[!UICONTROL MySQL]** >に移動し **[!UICONTROL MySQL Server 5.1]****[!UICONTROL MySQL Command Line Client]** ます。
1. パスワードを入力した後、次のSQLスクリプトを実行して、Webアプリケーションを介した接続を確立するため `dbuser` のユーザーアカウントを追加し、データベーススキーマを作成します（最後に「;」がないことを確認してください）。 Enterキーを押すだけ)。

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. テスト用にデータが含まれるようにテーブルのサンプルデータを入力するスクリプトを編集します。 [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. このスクリプトを実行して、手順2と同様にデータを入力します。

>[!NOTE]
>
>初めてスクリプトを実行すると、次の [!DNL CreateSampleDB.sql] エラーが表示されます。

*エラー1396 (HY000):&#39;dbuser&#39;@&#39;localhost&#39;クエリOKの操作DROP USERが失敗しました。0行が影響を受けます（0.00秒）。*

このエラーは無視して構いません。 これは、このスクリプトを初めて実行したときにのみ発生します。

この時点で、データベース接続プール(DBCP)を設定する必要があります。 DBCPは、ジャカルタ — コモンズデータベース接続プールを使用します。 JNDI Datasource TestDBは、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続をlocalhost上にないMySQLサーバーを指すように変更するには、にある [!DNL META-INF\context.xml] ファイル（ライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定）を変更する [!DNL flashaccess.war]か、更新したファイルを使用してWARファイルを変更 [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] して再作成します。 これらのパラメーターのいずれかを変更するには、WebContentディレクトリに [!DNL context.xml] あるを編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソース設定を変更します。

Eclipse内でリファレンス実装プロジェクトをデバッグする場合は、実行/デバッグ設定 `$CATALINA_HOME\lib\tomcat-dbcp.jar` にを追加する必要があります。 この手順は、スタンドアロンのTomcat 6.0サーバーで [!DNL flashaccess.war] ファイルを実行する場合は不要です。
