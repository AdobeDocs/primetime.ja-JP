---
title: データベースの設定と JNDI データソースの設定
description: データベースの設定と JNDI データソースの設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# データベースの設定と JNDI データソースの設定 {#setting-up-the-database-and-configuring-the-jndi-datasource}

参照実装ライセンスサーバーでは、以下の機能をサポートするデータベースが必要です。

* ユーザー認証
* 使用状況モデルデモビジネスルール
* メタデータの変換
* ドメインのサポート

匿名ライセンスの取得では、データベースを実行する必要はありません。

>[!NOTE]
>
>この節の手順は、Microsoft Windows プラットフォーム向けです。 その他のオペレーティングシステムについては、ご使用のオペレーティングシステムのドキュメントを参照するか、MySQL のドキュメントを参照してください。

ライセンスサーバーを実行するには、MySQL 5.1.34 をインストールして設定する必要があります。

1. MySQL インストーラーを実行します (DVD の Third Party\MySQL\Installer\5.1フォルダーにあります )。
1. インストール手順の最後で、 **[!UICONTROL Configure MySQL Server Now]** をクリックして、設定ウィザードを起動します。 デフォルト設定を使用するか、テスト目的で特定の設定を選択します。ただし、5 番目の画面では、次の設定を選択する必要があります。 **[!UICONTROL Online Transaction Processing (OLTP)]** または **[!UICONTROL Manual Setting]** および許可される最大接続数を入力します。

1. ルートパスワードをメモしておきます。
1. MySQL を再インストールする必要がある場合は、次の手順に従って、後でサーバーを起動する際の問題を回避します。

   * フォルダーを削除 *システムドライブ：* [!DNL \Documents and Settings\All Users\Application Data\MySQL].

   * 古い MySQL install フォルダー（例： ）を削除します。 *システムドライブ：* [!DNL \Program Files\MySQL\MySQL Server 5.1].

次に、MySQL JDBC Driver 5.1.7 をインストールする必要があります。これをおこなうには、 [!DNL mysql-connector-java-5.1.7-bin.jar] ( [!DNL Third Party\MySQL\Installer\5.1] DVD) から Tomcat サーバー lib ディレクトリへのフォルダ： [!DNL ...\Tomcat6.0\lib].

>[!NOTE]
>
>MySQL JDBC Driver 5.1.7 は、Tomcat 6.0 で動作します。古いバージョンの Tomcat はサポートされていません。

データベーススキーマを設定し、データベースにサンプルデータを入力して、サンプルデータベースを設定します。 これをおこなうには、次の手順を実行します。

1. に移動します。  **[!UICONTROL Window's Start Menu]** > **[!UICONTROL MySQL]** > **[!UICONTROL MySQL Server 5.1]** > **[!UICONTROL MySQL Command Line Client]** .
1. パスワードを入力した後、次の SQL スクリプトを実行してユーザーアカウントを追加します `dbuser` web アプリケーションを介した接続を確立し、データベーススキーマを作成する場合（末尾に「;」がないことを確認してください）。 Enter キーを押すだけです。)

   ```
       mysql> source “Reference Implementation\Server\dbscript\createsampledb.sql”
   ```

1. テスト目的でデータを含めるようにテーブルのサンプルデータを入力するスクリプトを編集します。 [!DNL Reference Implementation\Server\dbscript\PopulateSampleDB.sql].
1. このスクリプトを実行して、手順 2 のとおりにデータを入力します。

>[!NOTE]
>
>を初めて実行したとき [!DNL CreateSampleDB.sql] 次のエラーが発生するスクリプト：

*エラー 1396 (HY000): &#39;dbuser&#39;@&#39;localhost&#39;クエリ OK の操作 DROP USER が失敗しました。0 行が影響を受けました（0.00 秒）。*

このエラーは無視しても問題ありません。 これは、このスクリプトを初めて実行したときにのみ発生します。

この時点で、データベース接続プール (DBCP) を設定する必要があります。 DBCP は、Jakarta-Commons Database Connection Pool を使用します。 JNDI Datasource TestDB は、このアプリケーションサーバー接続プールを利用するように設定されています。 データベース接続をローカルホスト上にない MySQL サーバーを指すように変更するには、 [!DNL META-INF\context.xml] 次の場所にあるファイル（ライセンスサーバのデータベースの場所、ユーザー名、パスワードを指定） [!DNL flashaccess.war]、または変更 [!DNL \Reference Implementation\Server\refimpl\WebContent\META-INF\context.xml] 更新されたファイルを使用して WAR ファイルを再作成します。 これらのパラメーターのいずれかを変更するには、 [!DNL context.xml] WebContent ディレクトリに配置され、Ant スクリプトを使用して WAR ファイルを再作成します。 データベースを調整するには、このファイルの JNDI データソース設定を変更します。

Eclipse 内で参照実装プロジェクトをデバッグする場合は、 `$CATALINA_HOME\lib\tomcat-dbcp.jar` を run/debug 設定に追加します。 この手順は、 [!DNL flashaccess.war] ファイルをスタンドアロンの Tomcat 6.0 サーバー上に置きます。
