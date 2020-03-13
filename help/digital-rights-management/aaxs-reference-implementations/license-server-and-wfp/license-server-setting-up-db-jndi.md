---
seo-title: データベースの設定とJNDIデータソースの設定
title: データベースの設定とJNDIデータソースの設定
uuid: 1326523f-c053-4169-a934-1b2d3907b1f4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# データベースの設定とJNDIデータソースの設定 {#setting-up-the-database-and-configuring-the-jndi-datasource}

次の機能をサポートするデータベースが、参照実装ライセンスサーバーに必要です。

* ユーザー認証
* 使用モデルデモビジネスルール
* メタデータの変換
* ドメインのサポート

匿名ライセンスの取得では、データベースを実行する必要はありません。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この節の説明は、Microsoft Windowsプラットフォーム向けです。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQLのドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQL 5.1.34をインストールして設定する必要があります。

1. MySQLインストーラーを実行します(DVDのThird Party\MySQL\Installer\5.1フォルダーにあります)。
1. インストール手順の最後で、構成ウィザードを **[!UICONTROL Configure MySQL Server Now]** 起動することを確認します。 デフォルトの設定を使用するか、テスト目的の特定の設定を選択します。ただし、5番目の画面では、またはを選択し、許可さ **[!UICONTROL Online Transaction Processing (OLTP)]** れる最 **[!UICONTROL Manual Setting]** 大接続数を入力する必要があります。

1. rootパスワードをメモしておきます。
1. MySQLを再インストールする必要がある場合は、次の手順に従って、後でサーバーを起動する際の問題を回避します。

   * フォルダシステムド *ライブの削除：*[!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * 古いMySQLインストールフォルダーを削除します。たとえば、次のよ *うに入力します。*[!DNL \Program Files\MySQL\MySQL Server 5.1].

次に、MySQL JDBC Driver 5.1.7をインストールする必要があります。これを行うには、(DVD上の [!DNL mysql-connector-java-5.1.7-bin.jar] フォルダにあ [!DNL Third Party\MySQL\Installer\5.1] る)をTomcatサーバーのlibディレクトリにコピーします。 [!DNL ...\Tomcat6.0\lib].

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>MySQL JDBC Driver 5.1.7は、Tomcat 6.0で動作します。古いバージョンのTomcatはサポートされていません。

データベーススキーマを設定し、データベースにサンプルデータを入力して、サンプルデータベースを設定します。 これを行うには、次の手順を実行します。

1. /// **[!UICONTROL Window's Start Menu]** に移 **[!UICONTROL MySQL]** 動し **[!UICONTROL MySQL Server 5.1]** ます **[!UICONTROL MySQL Command Line Client]** 。
1. パスワードを入力した後、次のSQLスクリプトを実行して、Webアプリケーションを介した接続を確立するためのユーザーアカウントを追加し、データベーススキーマを作成します（最後に「;」がないことを確認してください）。 `dbuser` Enterキーを押すだけです)。

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. テスト用のデータを含めるために、テーブルのサンプルデータを入力するスクリプトを編集します。 [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. このスクリプトを実行して、手順2と同様にデータを入力します。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>スクリプトを初めて実行する [!DNL CreateSampleDB.sql] と、次のエラーが表示されます。

*エラー1396 (HY000):&#39;dbuser&#39;@&#39;localhost&#39;クエリのDROP USER操作が失敗しました。0行が影響を受けます（0.00秒）。*

このエラーは無視して構いません。 これは、このスクリプトを初めて実行したときにのみ発生します。

この時点で、データベース接続プーリング(DBCP)を設定する必要があります。 DBCPは、ジャカルタコモンズデータベース接続プールを使用します。 JNDI Datasource TestDBは、このアプリケーションサーバーの接続プーリングを利用するように設定されています。 データベース接続をlocalhost上にないMySQLサーバーを指すように変更するには、にあるファイル（ライセンスサーバーのデータベースの場所、ユーザー名、パスワードを指定）を変更するか、更新したファイルを使用してWARファ [!DNL META-INF\context.xml][!DNL flashaccess.war][!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] イルを変更して再作成します。 これらのパラメーターを変更するには、WebContentディレ [!DNL context.xml] クトリ内のを編集し、Antスクリプトを使用してWARファイルを再作成します。 データベースを調整するには、このファイルのJNDIデータソースの設定を変更します。

Eclipse内で参照実装プロジェクトをデバッグする場合は、実行/デバッグ設 `$CATALINA_HOME\lib\tomcat-dbcp.jar` 定にを追加する必要があります。 この手順は、スタンドアロンのTomcat 6.0サー [!DNL flashaccess.war] バーでファイルを実行する場合は不要です。
